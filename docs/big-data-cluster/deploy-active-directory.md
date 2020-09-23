---
title: Развертывание в режиме Active Directory
titleSuffix: SQL Server Big Data Cluster
description: Узнайте, как обновлять кластеры больших данных SQL Server в домене Active Directory.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/04/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 345002bdf21ee13fc6d33c9cbc1e9938a8b58377
ms.sourcegitcommit: 1126792200d3b26ad4c29be1f561cf36f2e82e13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2020
ms.locfileid: "90076652"
---
# <a name="deploy-big-data-clusters-2019-in-active-directory-mode"></a>Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Этот документ объясняет, как развернуть кластер больших данных SQL Server в режиме проверки подлинности Active Directory. Для проверки подлинности кластер использует существующий домен AD.

>[!Note]
>До выпуска накопительного пакета обновления 5 (CU5) для SQL Server 2019 существовало ограничение для кластеров больших данных, позволявшее развернуть в домене Active Directory только один кластер. После выхода накопительного пакета обновления 5 (CU5) это ограничение было устранено. Дополнительные сведения о новых возможностях см. в разделе [Концепция: развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory](active-directory-deployment-background.md). Примеры в этой статье скорректированы в соответствии с обоими вариантами использования развертывания.

## <a name="background"></a>Историческая справка

Чтобы включить проверку подлинности Active Directory (AD), кластер больших данных автоматически создает пользователей, группы, учетные записи компьютеров и имена субъектов-служб (SPN), необходимые различным службам кластера. Чтобы обеспечить определенную автономность этих учетных записей и предоставить разрешения на определение областей, во время развертывания необходимо выбрать подразделение (OU), в котором будут созданы все объекты AD, связанные с кластером больших данных. Создайте это подразделение до развертывания кластера.

Чтобы автоматически создать все необходимые объекты в Active Directory, кластеру больших данных требуется во время развертывания учетная запись AD. Эта учетная запись должна иметь разрешения на создание пользователей, групп и учетных записей компьютеров в указанном подразделении.

>[!IMPORTANT]
>В зависимости от политики истечения срока действия паролей, заданной на контроллере домена, срок действия паролей для этих учетных записей может истечь. Политика истечения срока действия по умолчанию — 42 дня. Не существует механизма для смены учетных данных для всех учетных записей в BDC, поэтому кластер станет неработоспособным по истечении этого срока действия. Чтобы избежать этой проблемы, обновите политику срока действия учетных записей служб BDC, вследствие чего на контроллере домена не будет задан срок действия пароля. Это действие можно выполнить до или после истечения срока действия. В последнем случае Active Directory повторно активирует пароли с истекшим сроком действия.
>
>На рисунке ниже показано, где задать это свойство в ветке "Пользователи и компьютеры" Active Directory.
>
>:::image type="content" source="media/deploy-active-directory/image25.png" alt-text="Настройка политики срока действия паролей":::

Список учетных записей и групп AD см. в разделе [Автоматически созданные объекты Active Directory](active-directory-objects.md).

В описанных ниже действиях предполагается, что у вас уже есть контроллер домена Active Directory. Если у вас нет контроллера домена, полезные пошаговые инструкции содержатся в следующем [руководстве](https://social.technet.microsoft.com/wiki/contents/articles/37528.create-and-configure-active-directory-domain-controller-in-azure-windows-server.aspx).

## <a name="create-ad-objects"></a>Создание объектов AD

Перед развертыванием BDC с интеграцией AD выполните следующие действия.

1. Создайте подразделение (OU), в котором будут храниться все объекты AD кластера больших данных. Кроме того, при развертывании можно назначить существующее подразделение.
1. Создайте учетную запись AD для BDC или используйте существующую учетную запись и предоставьте этой учетной записи AD для кластера больших данных необходимые разрешения.

### <a name="create-a-user-in-ad-for-bdc-domain-service-account"></a>Создание пользователя в AD для учетной записи службы домена кластера больших данных

Для кластера больших данных требуется учетная запись с конкретными разрешениями. Прежде чем продолжать, убедитесь, что у вас есть учетная запись AD, или создайте новую учетную запись, которую кластер больших данных может использовать для настройки необходимых объектов.

Чтобы создать нового пользователя в AD, можно щелкнуть правой кнопкой мыши домен или подразделение и выбрать **Новый** > **пользователь**:

![image12](./media/deploy-active-directory/image12.png)

В этой статье мы будем называть этого пользователя *учетной записью службы домена кластера больших данных*.

### <a name="create-an-ou"></a>Создание подразделения

На контроллере домена откройте **Пользователи и компьютеры Active Directory**. На левой панели щелкните правой кнопкой мыши каталог, в котором нужно создать подразделение, и выберите команду **Создать**  \> **Подразделение**, а затем следуйте указаниям мастера, чтобы создать подразделение. Кроме того, можно создать подразделение с помощью PowerShell:

```powershell
New-ADOrganizationalUnit -Name "<name>" -Path "<Distinguished name of the directory you wish to create the OU in>"
```

В примерах, приведенных в этой статье, для имени подразделения используется значение `bdc`.

![image13](./media/deploy-active-directory/image13.png)

![image14](./media/deploy-active-directory/image14.png)

### <a name="set-permissions-for-an-ad-account"></a>Задание разрешений для учетной записи AD 

Независимо от того, создавали ли вы нового пользователя AD или использовали существующего, у него должны быть определенные разрешения. Это учетная запись пользователя, которую контроллер BDC будет использовать при присоединении кластера к AD.

Учетная запись службы домена BDC должна иметь возможность создавать пользователей, группы и учетные записи компьютеров в подразделении. В следующих шагах мы именуем учетную запись доменной службы BDC `bdcDSA`. Для этой учетной записи можно выбрать любое имя.

1. На контроллере домена откройте **Пользователи и компьютеры Active Directory**.

1. На панели слева перейдите к своему домену, а затем к подразделению, которое `bdc` будет использовать.

1. Щелкните подразделение правой кнопкой мыши и выберите пункт **Свойства**.

1. Перейдите на вкладку "Безопасность" (убедитесь, что выбран параметр **Дополнительные компоненты**, щелкнув правой кнопкой мыши подразделение и выбрав пункт **Вид**).

    ![image15](./media/deploy-active-directory/image15.png)

1. Щелкните **Добавить...** и добавьте пользователя **bdcDSA**

    ![image16](./media/deploy-active-directory/image16.png)

    ![image17](./media/deploy-active-directory/image17.png)

1. Выберите пользователя **bdcDSA** и снимите все разрешения, а затем нажмите **Дополнительно**

1. Нажмите кнопку **Добавить**

    ![image18](./media/deploy-active-directory/image18.png)

    - Нажмите **Выбрать субъект-службу**, вставьте **bdcDSA** и нажмите кнопку ОК

    - В поле **Тип** задайте значение **Разрешить**.

    - В поле **Применяется к** задайте **Этот объект и все объекты-потомки**

        ![image19](./media/deploy-active-directory/image19.png)

    - Прокрутите вниз и нажмите кнопку **Очистить все**

    - Снова прокрутите вверх и выберите:
       - **Чтение всех свойств**
       - **Запись всех свойств**
       - **Создание объектов "Компьютер"**
       - **Удаление объектов "Компьютер"**
       - **Создание объектов "Группа"**
       - **Удаление объектов "Группа"**
       - **Создание объектов "Пользователь"**
       - **Удаление пользовательских объектов**

    - Нажмите кнопку **ОК**.

- Нажмите кнопку **Добавить**

    - Нажмите **Выбрать субъект-службу**, вставьте **bdcDSA** и нажмите кнопку ОК

    - В поле **Тип** задайте значение **Разрешить**.

    - В поле **Применяется к** укажите **Объекты-потомки "Компьютер"**

    - Прокрутите вниз и нажмите кнопку **Очистить все**

    - Снова прокрутите вверх и выберите **Сбросить пароль**

    - Нажмите кнопку **ОК**.

- Нажмите кнопку **Добавить**

    - Нажмите **Выбрать субъект-службу**, вставьте **bdcDSA** и нажмите кнопку ОК

    - В поле **Тип** задайте значение **Разрешить**.

    - В поле **Применяется к** укажите **Объекты-потомки "Пользователь"**

    - Прокрутите вниз и нажмите кнопку **Очистить все**

    - Снова прокрутите вверх и выберите **Сбросить пароль**

    - Нажмите кнопку **ОК**.

- Еще два раза нажмите кнопку **ОК**, чтобы закрыть открытые диалоговые окна.

## <a name="prepare-deployment"></a>Подготовка развертывания

Чтобы развернуть BDC с интеграцией AD, необходимо предоставить дополнительные сведения для создания в AD связанных с кластером больших данных объектов.

Используя профиль `kubeadm-prod` (или `openshift-prod`, начиная с выхода накопительного пакета обновления 5 — CU5), вы автоматически получите заполнители для сведений о безопасности и конечных точках, которые требуются для интеграции с AD.

Кроме того, необходимо предоставить учетные данные, которые [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] будет использовать для создания необходимых объектов в AD. Эти учетные данные предоставляются в качестве переменных среды

## <a name="set-security-environment-variables"></a>Задание переменных среды безопасности

Следующие переменные среды предоставляют учетные данные для учетной записи доменной службы BDC, которая будет использоваться для настройки интеграции с AD. Эта учетная запись также используется BDC для обслуживания объектов AD, связанных с BDC, в дальнейшем.

```bash
export DOMAIN_SERVICE_ACCOUNT_USERNAME=<AD principal account name>
export DOMAIN_SERVICE_ACCOUNT_PASSWORD=<AD principal password>
```

## <a name="provide-security-and-endpoint-parameters"></a>Предоставление параметров безопасности и конечных точек

В дополнение к переменным среды для учетных данных вам также потребуется предоставить сведения о безопасности и конечных точках, чтобы интеграция с AD функционировала. Необходимые параметры автоматически предоставляются в составе [профиля развертывания](deployment-guidance.md#configfile) `kubeadm-prod`/`openshift-prod`.

Для интеграции с AD требуются следующие параметры. Добавьте эти параметры в файлы `control.json` и `bdc.json` с помощью команд `config replace`, показанных ниже в этой статье. Во всех примерах ниже используется пример домена `contoso.local`.

- `security.activeDirectory.ouDistinguishedName`: различающееся имя подразделения (OU), в которое будут добавлены все учетные записи AD, созданные при развертывании кластера. Если домен называется `contoso.local`, различающееся имя подразделения имеет вид: `OU=BDC,DC=contoso,DC=local`.

- `security.activeDirectory.dnsIpAddresses`: содержит список IP-адресов DNS-серверов домена. 

- `security.activeDirectory.domainControllerFullyQualifiedDns`: Список полных доменных имен контроллера домена. Полное доменное имя содержит название компьютера/узла контроллера домена. Если у вас несколько контроллеров доменов, список можно указать здесь. Например, `HOSTNAME.CONTOSO.LOCAL`.

  > [!IMPORTANT]
  > Когда несколько контроллеров домена обслуживают домен, используйте основной контроллер домена (PDC) в качестве первой записи в списке `domainControllerFullyQualifiedDns` в конфигурации безопасности. Чтобы получить имя основного контроллера домена, введите `netdom query fsmo` в командной строке и нажмите клавишу **ВВОД**.

- `security.activeDirectory.realm` **Необязательный параметр**: в большинстве случаев область равна доменному имени. Для случаев, когда они не совпадают, используйте этот параметр для определения имени области (например, `CONTOSO.LOCAL`). Значение, указанное для этого параметра, должно быть полным.

  > [!IMPORTANT]
  > В настоящее время BDC не поддерживает конфигурацию, в которой имя домена Active Directory отличается от имени **NETBIOS** домена Active Directory.

- `security.activeDirectory.domainDnsName`: Имя домена DNS, которое будет использоваться для кластера (например, `contoso.local`).

- `security.activeDirectory.clusterAdmins`: этот параметр принимает одну группу AD. Область действия группы AD должна быть универсальной или глобальной. Члены этой группы будут иметь роль кластера *bdcAdmin*, которая предоставит им разрешения администратора в кластере. Это означает, что у них есть [разрешения `sysadmin` в SQL Server](../relational-databases/security/authentication-access/server-level-roles.md#fixed-server-level-roles), [разрешения `superuser` в HDFS](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsPermissionsGuide.html#The_Super-User) и разрешения администратора при подключении к конечной точке контроллера.

  >[!IMPORTANT]
  >Создайте эту группу в AD перед началом развертывания. Если область для этой группы AD является локальной доменной, развертывание завершается сбоем.

- `security.activeDirectory.clusterUsers`: Список групп AD, которые являются обычными пользователями (без прав администратора) в кластере больших данных. Список может включать группы AD, областью действия которых является универсальная или глобальная группа. Они не могут быть локальными доменными группами.

Группы Active Directory в этом списке сопоставлены с ролью кластера больших данных *bdcUser*, и им необходимо предоставить доступ к SQL Server (см. раздел [разрешения SQL Server](../relational-databases/security/permissions-hierarchy-database-engine.md)) или HDFS (см. [руководство по разрешениям HDFS](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsPermissionsGuide.html#:~:text=Permission%20Checks%20%20%20%20Operation%20%20,%20%20N%2FA%20%2029%20more%20rows%20)). При подключении к конечной точке контроллера эти пользователи могут получить только список конечных точек, доступных в кластере, с помощью команды *azdata bdc endpoint list*.

Дополнительные сведения об обновлении групп AD для этих параметров см. в разделе [Управление доступом к кластеру больших данных в режиме Active Directory](manage-user-access.md).

  >[!TIP]
  >Чтобы включить средства просмотра HDFS при подключении к узлу SQL Server Master в Azure Data Studio, пользователю с ролью bdcUser должны быть предоставлены разрешения VIEW SERVER STATE, так как Azure Data Studio использует DMV *sys.dm_cluster_endpoints*, чтобы получить необходимую конечную точку шлюза Knox для подключения к HDFS.

  >[!IMPORTANT]
  >Создайте эти группы в AD перед началом развертывания. Если область для любой из этих групп AD является локальной доменной, развертывание завершается сбоем.

  >[!IMPORTANT]
  >Если пользователи домена имеют большое количество членств в группах, следует настроить значения параметров шлюза *httpserver.requestHeaderBuffer* (значение по умолчанию — *8192*) и HDFS *hadoop.security.group.mapping.ldap.search.group.hierarchy.levels* (значение по умолчанию — *10*) с помощью пользовательского файла конфигурации развертывания *bdc.json*. Это позволяет избежать истечения времени ожидания подключения к шлюзу и/или получения HTTP-ответов с кодом состояния 431 (*Слишком большие поля заголовка запроса*). Ниже приведен раздел файла конфигурации, в котором показано, как определить значения этих параметров и каковы рекомендуемые значения для большего числа членств в группах. 

```json
{
    ...
    "spec": {
        "resources": {
            ...
            "gateway": {
                "spec": {
                    "replicas": 1,
                    "endpoints": [{...}],
                    "settings": {
                        "gateway-site.gateway.httpserver.requestHeaderBuffer": "65536"
                    }
                }
            },
            ...
        },
        "services": {
            ...
            "hdfs": {
                "resources": [...],
                "settings": {
                  "core-site.hadoop.security.group.mapping.ldap.search.group.hierarchy.levels": "4"
                }
            },
            ...
        }
    }
}
```

  >[!IMPORTANT]
  >Перед началом развертывания создайте в AD группы, указанные для параметров ниже. Если область для любой из этих групп AD является локальной доменной, развертывание завершается сбоем.

- `security.activeDirectory.appOwners` **Необязательный параметр**: список групп AD, имеющих разрешения на создание, удаление и запуск любого приложения. Список может включать группы AD, областью действия которых является универсальная или глобальная группа. Они не могут быть локальными доменными группами.

- `security.activeDirectory.appReaders` **Необязательный параметр**: список групп AD, имеющих разрешения на запуск любого приложения. Список может включать группы AD, областью действия которых является универсальная или глобальная группа. Они не могут быть локальными доменными группами.

Приведенная ниже таблица показывает модель авторизации для управления приложениями.

|   Авторизованные роли   |   Команда azdata   |
|----------------------|--------------------|
|   appOwner           | azdata app create  |
|   appOwner           | azdata app update  |
|   appOwner, appReader| azdata app list    |
|   appOwner, appReader| azdata app describe|
|   appOwner           | azdata app delete  |
|   appOwner, appReader| azdata app run     |

- `security.activeDirectory.subdomain`: **необязательный параметр**. Этот параметр появился в накопительном пакете обновления 5 (CU5) для SQL Server 2019 для поддержки развертывания нескольких кластеров больших данных в одном домене. С помощью этого параметра можно указать разные DNS-имена для каждого развернутого кластера больших данных. Если значение этого параметра не указано в разделе Active Directory файла `control.json`, по умолчанию для расчета значения параметра поддомена будет использоваться имя кластера больших данных (то же, что и имя пространства имен Kubernetes). 

  >[!NOTE]
  >Значение, передаваемое через параметр поддомена, является не новым доменом AD, а лишь DNS-доменом, который используется кластером больших данных для внутренних целей.

  >[!IMPORTANT]
  >Чтобы использовать эти новые возможности и развернуть несколько кластеров больших данных в одном домене, необходимо установить последнюю версию или обновить **CLI azdata**, чтобы она соответствовала накопительному пакету обновления 5 (CU5) для SQL Server 2019.

  Дополнительные сведения о развертывании нескольких кластеров больших данных в одном домене Active Directory см. в разделе [Концепция: развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory](active-directory-deployment-background.md).

- `security.activeDirectory.accountPrefix`: **необязательный параметр**. Этот параметр появился в накопительном пакете обновления 5 (CU5) для SQL Server 2019 для поддержки развертывания нескольких кластеров больших данных в одном домене. Этот параметр гарантирует уникальность имен учетных записей для различных служб кластеров больших данных, которые должны различаться между двумя кластерами. Настройка имени префикса учетной записи является необязательной; по умолчанию в качестве префикса учетной записи используется имя поддомена. Если имя поддомена длиннее 12 символов, в качестве префикса учетной записи используются первые 12 символов имени поддомена.  

  >[!NOTE]
  >Длина имени учетной записи Active Directory должна составлять не более 20 символов. Кластеру больших данных необходимо использовать 8 символов для различения объектов pod и наборов с отслеживанием состояния. В итоге остается 12 символов для префикса учетной записи.

[Проверьте область группы AD](/powershell/module/activedirectory/get-adgroup?view=winserver2012-ps&viewFallbackFrom=winserver2012r2-ps), чтобы определить, является ли она DomainLocal.

Если вы еще не выполнили инициализацию файла конфигурации развертывания, можно выполнить эту команду, чтобы получить копию конфигурации. В приведенных ниже примерах используется профиль `kubeadm-prod`, то же касается и `openshift-prod`.

```bash
azdata bdc config init --source kubeadm-prod  --target custom-prod-kubeadm
```

Чтобы задать указанные выше параметры в файле `control.json`, используйте следующие команды `azdata`. Эти команды заменяют конфигурацию и предоставляют ваши значения до развертывания.

> [!IMPORTANT]
> В выпуске SQL Server 2019 CU2 немного изменилась структура раздела конфигурации безопасности в профиле развертывания, и все связанные с Active Directory параметры находятся в новом *activeDirectory* в дереве JSON в разделе *security* в файле *control.json*.

>[!NOTE]
> Помимо предоставления различных значений для поддомена, как описано в этом разделе, необходимо также использовать разные номера портов для конечных точек кластера больших данных при развертывании нескольких кластеров больших данных в одном кластере Kubernetes. Эти номера портов можно настроить во время развертывания с помощью профилей [конфигурации развертывания](deployment-custom-configuration.md).

Приведенный ниже пример основан на использовании SQL Server 2019 CU2. В нем показана замена значений параметров, связанных с AD, в конфигурации развертывания. В сведениях о домене ниже приведены примеры значений.

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.clusterUsers=[\"bdcusersgroup\"]"
#Example for providing multiple clusterUser groups: [\"bdcusergroup1\",\"bdcusergroup2\"]
```

Кроме того (только после выхода накопительного пакета обновления 5 (CU5) для SQL Server 2019), вы можете переопределить значения по умолчанию для параметров `subdomain` и `accountPrefix`.

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.subdomain=[\"bdctest\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.accountPrefix=[\"bdctest\"]"
```

Аналогичным образом, в выпусках, предшествующих SQL Server 2019 CU2, можно запустить:

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterUsers=[\"bdcusersgroup\"]"
#Example for providing multiple clusterUser groups: [\"bdcusergroup1\",\"bdcusergroup2\"]
```

Помимо указанных выше сведений необходимо также указать DNS-имена для разных конечных точек кластера. Записи DNS, использующие указанные DNS-имена, будут автоматически созданы на DNS-сервере при развертывании. Эти имена будут использоваться при подключении к разным конечным точкам кластера. Например, если DNS-имя для главного экземпляра SQL имеет значение `mastersql`, а поддомен будет использовать значение по умолчанию имени кластера в *control.json*, вы будете использовать `mastersql.contoso.local,31433` или `mastersql.mssql-cluster.contoso.local,31433` (в зависимости от значений, указанных в файлах конфигурации развертывания для DNS-имен конечных точек) для подключения к главному экземпляру из этих средств. 

```bash
# DNS names for BDC services
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[0].dnsName=<controller DNS name>.contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[1].dnsName=<monitoring services DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[0].dnsName=<SQL Master Primary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[1].dnsName=<SQL Master Secondary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].dnsName=<Gateway (Knox) DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].dnsName=<app proxy DNS name>.<Domain name. e.g. contoso.local>"
```

> [!IMPORTANT]
> Можно использовать собственные DNS-имена конечных точек, если они полностью определены и не конфликтуют между любыми двумя кластерами больших данных, развернутыми в одном домене. При необходимости можно использовать значение параметра `subdomain`, чтобы гарантировать, что DNS-имена различаются в разных кластерах. Пример:

```bash
# DNS names for BDC services
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[0].dnsName=<controller DNS name>.<subdomain e.g. mssql-cluster>.contoso.local"
```

Здесь вы найдете пример скрипта для [развертывания кластера больших данных SQL Server в кластере Kubernetes с одним узлом (kubeadm) и интеграцией с AD](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm-ad).

> [!Note]
> В некоторых ситуациях вы не можете использовать новый параметр `subdomain`. Например, необходимо развернуть выпуск до выхода накопительного пакета обновления 5 (CU5), и вы уже обновили **CLI azdata**. Это маловероятно, но, если необходимо вернуться к поведению до выхода накопительного пакета обновления 5 (CU5), можно задать для параметра `useSubdomain` значение `false` в разделе `control.json` Active Directory.  Ниже приведена соответствующая команда.

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.useSubdomain=false"
```

На данный момент у вас должны быть заданы все необходимые параметры для развертывания BDC с интеграцией с Active Directory.

Теперь можно развернуть кластер BDC, интегрированный с Active Directory, с помощью команды `azdata` и профиля развертывания kubeadm-prod. Полную документацию по развертыванию [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] см. в разделе [Развертывание кластеров больших данных SQL Server в Kubernetes](deployment-guidance.md).

## <a name="verify-reverse-dns-entry-for-domain-controller"></a>Проверка обратной DNS-записи для контроллера домена

Убедитесь в наличии обратной DNS-записи (записи PTR) для самого доменного контроллера, зарегистрированного на сервере DNS. Это можно проверить, выполнив команду `nslookup` для доменного имени на контроллере домена, чтобы убедиться, что она разрешается в IP-адрес контроллера домена.

## <a name="connect-to-cluster-endpoints-in-ad-mode"></a>Подключение к конечным точкам кластера в режиме AD

Войдите в основной экземпляр SQL Server, используя проверку подлинности AD.

Чтобы проверить подключения AD к экземпляру SQL Server, подключитесь к основному экземпляру SQL с помощью `sqlcmd` При развертывании для подготовленных групп автоматически создаются данные для входа (`clusterUsers` и `clusterAdmins`).

Если вы используете Linux, сначала запустите `kinit` от имени пользователя AD, а затем запустите `sqlcmd`. Если вы используете Windows, просто войдите в систему от имени нужного пользователя с **подключенного к домену клиентского компьютера**.

### <a name="connect-to-master-instance-from-linuxmac"></a>Подключение к основному экземпляру из Linux или Mac

```bash
kinit <username>@<domain name>
sqlcmd -S <DNS name for master instance>,31433 -E
```

### <a name="connect-to-master-instance-from-windows"></a>Подключение к основному экземпляру из Windows

```cmd
sqlcmd -S <DNS name for master instance>,31433 -E
```

### <a name="log-in-to-sql-server-master-instance-using-azure-data-studio-or-ssms"></a>Вход в основной экземпляр SQL Server с использованием Azure Data Studio или SSMS

Из подключенного к домену клиента можно открыть SSMS или Azure Data Studio и подключиться к основному экземпляру. Процедура схожа с подключением к любому экземпляру SQL Server с использованием проверки подлинности AD.

С помощью SSMS:

![image23](./media/deploy-active-directory/image23.png)

С помощью Azure Data Studio:

![image24](./media/deploy-active-directory/image24.png)}

### <a name="log-in-to-controller-with-ad-authentication"></a>Вход в контроллер с проверкой подлинности AD

#### <a name="connect-to-controller-with-ad-authentication-from-linuxmac"></a>Подключение к контроллеру с помощью проверки подлинности AD из Linux или Mac

Существует два варианта подключения к конечной точке контроллера, используя `azdata` и проверку подлинности AD. Можно использовать параметр *--endpoint/-e*.

```bash
kinit <username>@<domain name>
azdata login -e https://<controller DNS name>:30080 --auth ad
```

Кроме того, можно подключиться с использованием параметра *--namespace/-n*, который является именем кластера больших данных.

```bash
kinit <username>@<domain name>
azdata login -n <clusterName> --auth ad
```

#### <a name="connect-to-controller-with-ad-authentication-from-windows"></a>Подключение к контроллеру с проверкой подлинности AD из Windows

```cmd
azdata login -e https://<controller DNS name>:30080 --auth ad
```

### <a name="use-ad-authentication-to-knox-gateway-webhdfs"></a>Использование проверки подлинности AD для шлюза Knox (webHDFS)

Отправлять команды HDFS также можно через конечную точку шлюза Knox с помощью curl. Для этого требуется проверка подлинности AD в Knox. Приведенная ниже команда curl отправляет вызов webHDFS REST через шлюз Knox для создания каталога `products`

```bash
curl -k -v --negotiate -u : https://<Gateway DNS name>:30443/gateway/default/webhdfs/v1/products?op=MKDIRS -X PUT
```

## <a name="known-issues-and-limitations"></a>Известные проблемы и ограничения

**Ограничения, которые следует учитывать в накопительном пакете обновления 5 (CU5) для SQL Server 2019**

- В настоящее время информационная панель поиска журналов и информационная панель метрик не поддерживают проверку подлинности AD. Для проверки подлинности на этих информационных панелях можно использовать базовые имя пользователя и пароль, заданные при развертывании. Все остальные конечные точки кластера поддерживают проверку подлинности AD.

- Сейчас безопасный режим AD будет работать только в средах развертывания `kubeadm` и `openshift`, но не в AKS или ARO. Профили развертывания `kubeadm-prod` и `openshift-prod` по умолчанию включают разделы, посвященные безопасности.

- До выпуска накопительного пакета обновления 5 (CU5) для SQL Server 2019, разрешен всего один кластер больших данных на домен (Active Directory). Поддержка нескольких кластеров больших данных на домен доступна, начиная с выпуска накопительного пакета обновления 5 (CU5).

- Ни одна из групп AD, указанных в конфигурациях безопасности, не может быть в области DomainLocal. Вы можете проверить область группы AD, выполнив [эти инструкции](/powershell/module/activedirectory/get-adgroup?view=winserver2012-ps&viewFallbackFrom=winserver2012r2-ps).

- Учетная запись AD, которая может использоваться для входа в кластер больших данных, разрешена из того же домена, который был настроен для кластера больших данных. Поддержка входов из другого доверенного домена не планируется.

## <a name="next-steps"></a>Дальнейшие действия

[Устранение неполадок при интеграции кластера больших данных SQL Server с Active Directory](troubleshoot-active-directory.md)

[Концепция: развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory](active-directory-deployment-background.md)
