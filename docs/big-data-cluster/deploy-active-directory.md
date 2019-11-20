---
title: Развертывание кластера больших данных SQL Server в режиме Active Directory
titleSuffix: Deploy SQL Server Big Data Cluster in Active Directory mode
description: Узнайте, как обновлять кластеры больших данных SQL Server в домене Active Directory.
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 11/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 40b1101d9ee6c57db865282d1556f96aa4311a1f
ms.sourcegitcommit: 02b7fa5fa5029068004c0f7cb1abe311855c2254
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2019
ms.locfileid: "74127449"
---
# <a name="deploy-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-in-active-directory-mode"></a>Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом документе описывается развертывание кластера больших данных (BDC) SQL Server 2019 в режиме проверки подлинности Active Directory, подразумевающем использование для проверки подлинности существующего домена AD.

## <a name="background"></a>Историческая справка

Чтобы включить проверку подлинности Active Directory (AD), кластер больших данных автоматически создает пользователей, группы, учетные записи компьютеров и имена субъектов-служб (SPN), необходимые различным службам кластера. Чтобы обеспечить определенную автономность этих учетных записей и предоставить разрешения на определение областей, во время развертывания необходимо назначить подразделение (OU), в котором будут созданы все объекты AD, связанные с кластером больших данных. Создайте это подразделение до развертывания кластера.

Чтобы автоматически создать все необходимые объекты в Active Directory, кластеру больших данных требуется во время развертывания учетная запись AD. Эта учетная запись должна иметь разрешения на создание пользователей, групп и учетных записей компьютеров в указанном подразделении.

В описанных ниже действиях предполагается, что у вас уже есть контроллер домена Active Directory. Если у вас нет контроллера домена, полезные пошаговые инструкции содержатся в следующем [руководстве](https://social.technet.microsoft.com/wiki/contents/articles/37528.create-and-configure-active-directory-domain-controller-in-azure-windows-server.aspx).

## <a name="create-ad-objects"></a>Создание объектов AD

Перед развертыванием BDC с интеграцией AD выполните следующие действия.

1. Создайте подразделение (OU), в котором будут храниться все объекты AD кластера больших данных. Кроме того, для этого при развертывании можно назначить существующее подразделение.
1. Создайте учетную запись AD для BDC или используйте существующую учетную запись и предоставьте этой учетной записи AD для кластера больших данных необходимые разрешения.

### <a name="create-a-user-in-ad-for-bdc-domain-service-account"></a>Создание пользователя в AD для учетной записи службы домена кластера больших данных

Для кластера больших данных требуется учетная запись с конкретными разрешениями. Прежде чем продолжать, убедитесь, что у вас есть учетная запись AD, или создайте новую учетную запись, которую кластер больших данных может использовать для настройки необходимых объектов.

Чтобы создать нового пользователя в AD, можно щелкнуть правой кнопкой мыши домен или подразделение и выбрать **Новый** > **пользователь**:

![image12](./media/deploy-active-directory/image12.png)

В этой статье мы будем называть этого пользователя *учетной записью службы домена кластера больших данных*.

### <a name="creating-an-ou"></a>Создание подразделения

На контроллере домена откройте **Пользователи и компьютеры Active Directory**. На левой панели щелкните правой кнопкой мыши каталог, в котором нужно создать подразделение, и выберите команду \>Создать **подразделение**, а затем следуйте указаниям мастера, чтобы создать подразделение. Кроме того, можно создать подразделение с помощью PowerShell:

```powershell
New-ADOrganizationalUnit -Name "<name>" -Path "<Distinguished name of the directory you wish to create the OU in>"
```

В примерах, приведенных в этой статье, выполняется именование подразделения: `bdc`

![image13](./media/deploy-active-directory/image13.png)

![image14](./media/deploy-active-directory/image14.png)

### <a name="setting-permissions-the-bdc-ad-account"></a>Настройка разрешений для учетной записи AD кластера больших данных

Независимо от того, создавали ли вы нового пользователя AD или использовали существующего, у него должны быть определенные разрешения. Это учетная запись пользователя, которую контроллер BDC будет использовать при присоединении кластера к AD.

Учетная запись службы домена BDC должна иметь возможность создавать пользователей, группы и учетные записи компьютеров в подразделении. В следующих шагах мы именуем учетную запись доменной службы BDC `bdcDSA`. Для этой учетной записи можно выбрать любое имя.

1. На контроллере домена откройте **Пользователи и компьютеры Active Directory**.

1. На панели слева перейдите к своему домену, а затем к подразделению, которое `bdc` будет использовать.

1. Щелкните подразделение правой кнопкой мыши и выберите пункт **Свойства**.

1. Перейдите на вкладку "Безопасность" (убедитесь, что выбран параметр **Дополнительные компоненты**, щелкнув правой кнопкой мыши подразделение и выбрав пункт **Вид**).

    ![image15](./media/deploy-active-directory/image15.png)

1. Щелкните **Добавить...** и добавьте пользователя **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA**

    ![image16](./media/deploy-active-directory/image16.png)

    ![image17](./media/deploy-active-directory/image17.png)

1. Выберите пользователя **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA** и снимите все разрешения, а затем нажмите **Дополнительно**

1. Нажмите кнопку **Добавить**

    ![image18](./media/deploy-active-directory/image18.png)

    - Нажмите **Выбрать субъект-службу**, вставьте **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA** и нажмите кнопку ОК.

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

    - Нажмите **Выбрать субъект-службу**, вставьте **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA** и нажмите кнопку ОК.

    - В поле **Тип** задайте значение **Разрешить**.

    - В поле **Применяется к** укажите **Объекты-потомки "Компьютер"**

    - Прокрутите вниз и нажмите кнопку **Очистить все**

    - Снова прокрутите вверх и выберите **Сбросить пароль**

    - Нажмите кнопку **ОК**.

- Нажмите кнопку **Добавить**

    - Нажмите **Выбрать субъект-службу**, вставьте **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA** и нажмите кнопку ОК.

    - В поле **Тип** задайте значение **Разрешить**.

    - В поле **Применяется к** укажите **Объекты-потомки "Пользователь"**

    - Прокрутите вниз и нажмите кнопку **Очистить все**

    - Снова прокрутите вверх и выберите **Сбросить пароль**

    - Нажмите кнопку **ОК**.

- Еще два раза нажмите кнопку **ОК**, чтобы закрыть открытые диалоговые окна.

## <a name="prepare-deployment"></a>Подготовка развертывания

Чтобы развернуть BDC с интеграцией AD, необходимо предоставить дополнительные сведения для создания в AD связанных с кластером больших данных объектов.

Используя профиль `kubeadm-prod`, вы автоматически получите заполнители для сведений о безопасности и конечных точках, которые требуются для интеграции в AD.

Кроме того, необходимо предоставить учетные данные, которые [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] будет использовать для создания необходимых объектов в AD. Эти учетные данные предоставляются в качестве переменных среды

## <a name="set-security-environment-variables"></a>Задание переменных среды безопасности

Следующие переменные среды предоставляют учетные данные для учетной записи доменной службы BDC, которая будет использоваться для настройки интеграции с AD. Эта учетная запись также используется BDC для обслуживания объектов AD, связанных с BDC, в дальнейшем.

```bash
export DOMAIN_SERVICE_ACCOUNT_USERNAME=<AD principal account name>
export DOMAIN_SERVICE_ACCOUNT_PASSWORD=<AD principal password>
```

## <a name="provide-security-and-endpoint-parameters"></a>Предоставление параметров безопасности и конечных точек

В дополнение к переменным среды для учетных данных вам также потребуется предоставить сведения о безопасности и конечных точках, чтобы интеграция с AD функционировала. Необходимые параметры автоматически предоставляются в составе [профиля развертывания](deployment-guidance.md#configfile) `kubeadm-prod`.

Для интеграции с AD требуются следующие параметры. Добавьте эти параметры в файлы `control.json` и `bdc.json` с помощью команд `config replace`, показанных ниже в этой статье. Во всех примерах ниже используется пример домена `contoso.local`.

- `security.ouDistinguishedName`: различающееся имя подразделения (OU), в которое будут добавлены все учетные записи AD, созданные при развертывании кластера. Если домен называется `contoso.local`, различающееся имя подразделения имеет вид: `OU=BDC,DC=contoso,DC=local`.

- `security.dnsIpAddresses`: список IP-адресов контроллеров доменов

- `security.domainControllerFullyQualifiedDns`: Список полных доменных имен контроллера домена. Полное доменное имя содержит название компьютера/узла контроллера домена. Если у вас несколько контроллеров доменов, список можно указать здесь. Пример: `HOSTNAME.CONTOSO.LOCAL`

- `security.realm` **Необязательный параметр**: в большинстве случаев область равна доменному имени. Для случаев, когда они не совпадают, используйте этот параметр для определения имени области (например, `CONTOSO.LOCAL`).

- `security.domainDnsName`: имя домена (например, `contoso.local`).

- `security.clusterAdmins`: этот параметр принимает одну группу AD*. Члены этой группы получают в кластере разрешения администратора. Это означает, что у них будут разрешения системного администратора в SQL Server, разрешения суперпользователя в HDFS и разрешения администраторов в контроллере.

- `security.clusterUsers`: Список групп AD, которые являются обычными пользователями (без прав администратора) в кластере больших данных.

- `security.appOwners` **Необязательный параметр**: список групп AD, имеющих разрешения на создание, удаление и запуск любого приложения.

- `security.appReaders` **Необязательный параметр**: список пользователей или групп AD, имеющих разрешения на запуск любого приложения. 

Если вы еще не выполнили инициализацию файла конфигурации развертывания, можно выполнить эту команду, чтобы получить копию конфигурации.

```bash
azdata bdc config init --source kubeadm-prod  --target custom-prod-kubeadm
```

Чтобы задать указанные выше параметры в файле `control.json`, используйте следующие команды `azdata`. Эти команды заменяют конфигурацию и предоставляют ваши значения до развертывания.

В примере ниже заменяются значения параметров, связанные с AD, в конфигурации развертывания. В сведениях о домене ниже приведены примеры значений.

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterUsers=[\"bdcusersgroup\"]"
```

Помимо указанных выше сведений необходимо также указать DNS-имена для разных конечных точек кластера. Записи DNS, использующие указанные DNS-имена, будут автоматически созданы на DNS-сервере при развертывании. Эти имена будут использоваться при подключении к разным конечным точкам кластера. Например, если DNS-имя для основного экземпляра SQL Server — `mastersql`, для подключения к главному экземпляру с помощью средств будет использоваться значение `mastersql.contoso.local,31433`.

> [!NOTE]
> Убедитесь, что на DNS-сервере созданы DNS-записи для имен, которые вы определяете ниже. Для развертываний `kubeadm` при создании DNS-записей можно, например, использовать IP-адрес основного узла Kubernetes.

```bash
# DNS names for BDC services
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[0].dnsName=<controller DNS name>.contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[1].dnsName=<monitoring services DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[0].dnsName=<SQL Master Primary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[1].dnsName=<SQL Master Secondary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].dnsName=<Gateway (Knox) DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].dnsName=<app proxy DNS name>.<Domain name. e.g. contoso.local>"
```

Здесь вы найдете пример скрипта для [развертывания кластера больших данных SQL Server в кластере Kubernetes с одним узлом (kubeadm) и интеграцией с AD](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm-ad).

На данный момент у вас должны быть заданы все необходимые параметры для развертывания BDC с интеграцией с Active Directory.

Полную документацию по развертыванию [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] вы найдете в составе [официальной документации](deployment-guidance.md).

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

Можно подключиться к конечной точке контроллера, используя `azdata` и проверку подлинности AD.

```bash
kinit <username>@<domain name>
azdata login -e https://<controller DNS name>:30080 --auth ad
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

**Ограничения, которые следует учитывать в этом выпуске:**

- В настоящее время информационная панель поиска журналов и информационная панель метрик не поддерживают проверку подлинности AD. В дальнейшем планируется реализовать поддержку AD для этой конечной точки. Для проверки подлинности на этих информационных панелях можно использовать базовые имя пользователя и пароль, заданные при развертывании. Все остальные конечные точки кластера поддерживают проверку подлинности AD.

- Безопасный режим AD будет работать только в средах развертывания `kubeadm`, но не в AKS прямо сейчас. Профиль развертывания `kubeadm-prod` по умолчанию включает разделы, посвященные безопасности.

- В настоящее время допускается использовать не более одного кластера больших данных на домен. Реализация поддержки нескольких кластеров больших данных на домен планируется в будущем.
