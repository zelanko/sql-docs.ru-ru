---
title: Создание настраиваемого рабочего процесса (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 8e4403e9-595c-4b6b-9d0c-f6ae1b2bc99d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 63f8be6f47ef4a6abd20c42757648ca03a5701b3
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84962066"
---
# <a name="create-a-custom-workflow-master-data-services"></a>Создание настраиваемого рабочего процесса (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] использует бизнес-правила для создания таких базовых решений рабочего процесса, как автоматическое обновление и проверка данных, а также отправка уведомлений по электронной почте с учетом заданных условий. Когда требуется более сложная обработка, чем та, которую обеспечивают действия встроенного рабочего процесса, используйте пользовательский рабочий процесс. Пользовательский рабочий процесс ― это создаваемая вами сборка .NET. При вызове вашей сборки рабочего процесса код может выполнять любые действия, которые требуются в данной ситуации. Если рабочему процессу требуется сложная обработка событий, например многоуровневые утверждения или сложные деревья принятия решений, можно настроить [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] на запуск пользовательского рабочего процесса, который анализирует данные и определяет, куда их отправить для утверждения.  
  
## <a name="how-custom-workflows-are-processed"></a>Как обрабатываются пользовательские рабочие процессы  
 В обработку пользовательских рабочих процессов вовлечены три основных компонента: веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], служба SQL Server MDS Workflow Integration Service и сборка обработчика рабочих процессов. Эти компоненты обрабатывают пользовательский рабочий процесс следующим образом:  
  
1.  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] используется для проверки сущности, которая запускает рабочий процесс.  
  
2.  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] отправляет элементы, которые удовлетворяют условиям бизнес-правила, в очередь компонента Service Broker в базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
3.  Служба SQL Server MDS Workflow Integration Service через регулярные интервалы обращается к хранимой процедуре в базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
4.  Когда хранимая процедура находит записи в очереди компонента Service Broker, она возвращает их службе SQL Server MDS Workflow Integration Service.  
  
5.  Служба SQL Server Службы Integration Services MDS направляет данные в сборку обработчика рабочих процессов.  
  
> [!NOTE]  
>  Примечание. Служба SQL Server MDS Workflow Integration Service предназначена для запуска простых процессов. Если пользовательскому коду требуется сложная обработка, ее следует выполнить либо в отдельном потоке, либо за пределами обработки рабочего процесса.  
  
## <a name="configure-master-data-services-for-custom-workflows"></a>Настройка служб Master Data Services для пользовательских рабочих процессов  
 Для создания пользовательского рабочего процесса потребуется написать определенный объем пользовательского кода и настроить веб-приложение [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] на передачу данных рабочего процесса используемому обработчику рабочих процессов. Выполните следующие действия, чтобы включить обработку пользовательских рабочих процессов.  
  
1.  Создайте сборку .NET, которая реализует <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>.  
  
2.  Настройте службу SQL Server MDS Workflow Integration Service для соединения с базой данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], а также для связи тега с используемым обработчиком рабочих процессов.  
  
3.  Запустите службу SQL Server MDS Workflow Integration Service.  
  
4.  Создайте бизнес-правило в веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], которое запускает рабочий процесс, обозначенный именем используемого обработчика рабочих процессов.  
  
5.  Примените бизнес-правило к элементу, который запускает пользовательский рабочий процесс.  
  
### <a name="create-the-workflow-handler-assembly"></a>Создание сборки обработчика рабочих процессов  
 Пользовательский рабочий процесс представляет собой сборку библиотеки классов .NET, которая реализует интерфейс <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. Служба SQL Server MDS Workflow Integration Service обращается к методу <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> для выполнения кода. Пример кода, который реализует <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>, см. в разделе [Пример настраиваемого рабочего процесса (службы Master Data Services)](create-a-custom-workflow-example.md).  
  
 Выполните следующие действия, чтобы создать с помощью Visual Studio 2010 сборку, которую сможет вызывать служба SQL Server MDS Workflow Integration Service для обработки пользовательского рабочего процесса:  
  
1.  В Visual Studio 2010 создайте проект **Библиотека классов**, в котором используется язык по вашему выбору. Чтобы создать библиотеку классов C#, выберите типы проектов **Visual C#\Windows** и шаблон **Библиотека классов**. Введите имя проекта, например **MDSWorkflowTest**, и нажмите кнопку **ОК**.  
  
2.  Добавьте ссылку на файл Microsoft.MasterDataServices.WorkflowTypeExtender.dll. Эту сборку можно найти в \<Your installation folder> \Мастер данных Services\WebApplication\bin.  
  
3.  Добавьте строку "using Microsoft.MasterDataServices.Core.Workflow;" в файл с кодом C#.  
  
4.  В объявлении класса установите наследование от <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. Объявление класса должно выглядеть примерно так: public class WorkflowTester : IWorkflowTypeExtender.  
  
5.  Реализуйте интерфейс <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. Метод <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> вызывается службами SQL Server MDS Workflow Integration Service для запуска рабочего процесса.  
  
6.  Скопируйте сборку в расположение исполняемого файла SQL Server службы интеграции рабочих процессов MDS с именем Microsoft.MasterDataServices.Workflow.exe в \<Your installation folder> \Мастер Data Services\WebApplication\bin.  
  
### <a name="configure-sql-server-mds-workflow-integration-service"></a>Настройка службы Configure SQL Server MDS Workflow Integration Service  
 Измените файл конфигурации [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], включив в него данные соединения для базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], и свяжите тег со сборкой обработчика рабочих процессов, выполнив следующие действия.  
  
1.  Поиск Microsoft.MasterDataServices.Workflow.exe.config в \<Your installation folder> Services\WebApplication\bin. данных \Мастер  
  
2.  Добавьте сведения о подключении к базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в параметр ConnectionString. Если в установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются параметры сортировки, учитывающие регистр, то имя базы данных следует ввести в том же регистре, который используется в базе данных. Например, полный тег параметра может выглядеть следующим образом:  
  
    ```xml  
    <setting name="ConnectionString" serializeAs="String">  
        <value>Server=myServer;Database=myDatabase;Integrated Security=True</value>  
    </setting>  
    ```  
  
3.  Под параметром ConnectionString добавьте параметр WorkflowTypeExtenders, чтобы связать имя тега с используемой сборкой обработчика рабочих процессов. Пример:  
  
    ```xml  
    <setting name="WorkflowTypeExtenders" serializeAs="String">  
        <value>TEST=MDSWorkflowTestLib.WorkflowTester, MDSWorkflowTestLib</value>  
    </setting>  
    ```  
  
     Внутренний текст \<value> тега имеет вид \<Workflow tag> = \<assembly-qualified workflow type name> . \<Workflow tag>— Это имя, которое используется для задания сборки обработчика рабочего процесса при создании бизнес-правила в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . \<assembly-qualified workflow type name>— Это имя класса рабочего процесса с указанием пространства имен, за которым следует запятая, за которым следует отображаемое имя сборки. Если сборка имеет строгое имя, то также необходимо указать данные о версии и ее PublicKeyToken. \<setting>Если вы создали несколько обработчиков рабочих процессов для различных типов рабочих процессов, можно включить несколько тегов.  
  
> [!NOTE]  
>  В зависимости от конфигурации сервера при попытке сохранить файл Microsoft.MasterDataServices.Workflow.exe.config на экране может появиться сообщение об ошибке "В доступе отказано". В этом случае временно отключите контроль учетных записей на сервере. Для этого откройте панель управления и выберите пункт **Система и безопасность**. В разделе **Центр уведомлений** щелкните **Изменить параметры контроля учетных записей**. В диалоговом окне **Параметры контроля учетных записей** передвиньте ползунок в самый низ, чтобы не получать никаких уведомлений. Перезагрузите компьютер и повторите описанные ранее действия для изменения файла конфигурации. После сохранения файла, сбросьте параметры контроля учетных записей пользователей на значения по умолчанию.  
  
### <a name="start-sql-server-mds-workflow-integration-service"></a>Запуск службы SQL Server MDS Workflow Integration Service  
 По умолчанию служба SQL Server MDS Workflow Integration Service не установлена. Чтобы использовать эту службу, ее сначала необходимо установить. Для обеспечения наибольшей безопасности создайте локального пользователя для этой службы и предоставьте этому пользователю только те разрешения, которые необходимы для выполнения операций рабочего процесса. Чтобы создать пользователя, установите службу, запустите ее и выполните следующие действия.  
  
1.  С помощью диспетчера локальных пользователей и групп создайте локального пользователя с именем, например, mds_workflow_service.  
  
2.  С помощью среды SQL Server Management Studio предоставьте пользователю mds_workflow_service разрешение на выполнение хранимой процедуры [mdm].[udpExternalActionsGet]. Для этого создайте новое имя входа для учетной записи mds_workflow_service, создайте нового пользователя в базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], сопоставьте этого пользователя с именем входа mds_workflow_service и предоставьте ему разрешение EXECUTE для хранимой процедуры [mdm].[udpExternalActionsGet].  
  
3.  Предоставьте пользователю mds_workflow_service разрешение на выполнение сборки обработчика рабочих процессов. Для этого добавьте пользователя mds_workflow_service на вкладку **Безопасность** диалогового окна **Свойства** сборки обработчика рабочих процессов и предоставьте пользователю службы mds_workflow_service разрешение READ и EXECUTE.  
  
4.  Предоставьте пользователю службы mds_workflow_service разрешение на выполнение исполняемого файла службы SQL Server MDS Workflow Integration Service. Для этого добавьте mds_workflow_service пользователя на вкладку **Безопасность** **свойств** Microsoft.MasterDataServices.Workflow.exe, в поле \<Your installation folder> \Мастер Data Services\WebApplication\bin и предоставьте пользователю MDS_WORKFLOW_SERVICE разрешение на чтение и выполнение.  
  
5.  Установите службу SQL Server MDS Workflow Integration Service с помощью программы установки .NET с именем InstallUtil.exe. Программа InstallUtil.exe может находиться в установочной папке платформы .NET, например C:\Windows\Microsoft.NET\Framework\v4.0.30319\\. Установите службу SQL Server MDS Workflow Integration Service, введя в командной строке следующую команду:  
  
    ```  
    C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil Microsoft.MasterDataServices.Workflow.exe  
    ```  
  
     При запросе во время установки укажите пользователя mds_workflow_service.  
  
6.  Запустите службу SQL Server MDS Workflow Integration Service с помощью оснастки «Службы». Для этого найдите службу SQL Server MDS Workflow Integration Service в оснастке "Службы", выделите ее и щелкните ссылку **Запустить**.  
  
### <a name="create-a-workflow-business-rule"></a>Создание бизнес-правила рабочего процесса  
 С помощью веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] создайте и опубликуйте бизнес-правило, которое при его применении будет запускать рабочий процесс. Бизнес-правило должно содержать действия, которые изменяют значения атрибутов таким образом, чтобы после его применения правило не могло быть применено еще раз. Например, критерии бизнес-правила должны быть соблюдены, когда значение атрибута «Price» больше 500, а значение атрибута «Approved» не задано. В этом случае правило должно включать два действия: задание значения «Pending» атрибуту «Approved» и запуск рабочего процесса. Также можно создать правило, в котором будет использоваться условие "изменилось", и добавить атрибуты в группы отслеживания изменений. Дополнительные сведения о бизнес-правилах см. в статье [Бизнес-правила (службы Master Data Services)](../business-rules-master-data-services.md).  
  
 Создайте бизнес-правило, которое будет запускать пользовательский рабочий процесс в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], выполнив следующие действия.  
  
1.  В редакторе бизнес-правил [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , после того как вы указали условия бизнес-правила, перетащите действие **запустить рабочий процесс** из списка **внешние действия** в метку **действия** панели **then** .  
  
2.  На панели **Изменение действия** в поле **Тип рабочего процесса** введите тег, который обозначает сборку обработчика рабочего процесса. Это тег, который был задан в файле конфигурации сборки, например, TEST.  
  
3.  При необходимости установите флажок **Включить данные элемента**. Этот параметр устанавливается для того, чтобы включать имена атрибутов и значения из XML-файла, который передается обработчику рабочего процесса.  
  
4.  В поле **Сайт рабочего процесса** введите имя веб-сайта. Для пользовательского рабочего процесса это может и не применяться, но может быть использовано для формирования дополнительного контекста.  
  
5.  В поле **Имя рабочего процесса** введите имя рабочего процесса, которое указано в Visual Studio. Для пользовательского рабочего процесса это может и не применяться, но может быть использовано для формирования дополнительного контекста.  
  
6.  Сохраните и опубликуйте бизнес-правило.  
  
### <a name="apply-business-rules-to-start-a-workflow"></a>Применение бизнес-правила к запуску рабочего процесса  
 Примените бизнес-правило к данным, чтобы запустить рабочий процесс. Для этого с помощью веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] измените запись, содержащую элементы, которые требуется проверить. Нажмите кнопку **Применить бизнес-правила**. В ответ на бизнес-правило веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] заполняет очередь компонента Service Broker базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Когда служба SQL Server MDS Workflow Integration Service проверяет очередь, она отправляет данные указанной сборке обработчика рабочего процесса и очищает очередь. Сборка обработчика рабочего процесса выполняет те действия, которые были запрограммированы.  
  
## <a name="troubleshoot-custom-workflows"></a>Устранение неполадок пользовательских рабочих процессов  
 Если сборка обработчика рабочего процесса не получает данные, можно попробовать выполнить отладку службы SQL Server MDS Workflow Integration Service или просмотреть очередь компонента Service Broker.  
  
### <a name="debug-sql-server-mds-workflow-integration-service"></a>Отладка службы SQL Server MDS Workflow Integration Service  
 Для отладки службы SQL Server Workflow Integration Service выполните следующие действия.  
  
1.  С помощью оснастки «Службы» остановите службу.  
  
2.  Откройте командную строку, перейдите в каталог, в котором находится служба и запустите службу в пультовом режиме, введя следующую команду: Microsoft.MasterDataServices.Workflow.exe -console.  
  
3.  В веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] обновите элемент и примените бизнес-правило еще раз. В окне консоли будут отображены подробные записи журнала.  
  
### <a name="view-the-service-broker-queue"></a>Просмотр очереди компонента Service Broker  
 Очередь компонента Service Broker, в которой содержатся основные данные, переданные в рамках рабочего процесса, находится по адресу mdm.microsoft/mdm/queue/externalaction. В **обозревателе объектов** среды SQL Management Studio очереди находятся в узле компонента Service Broker базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Имейте в виду, что если служба должным образом очистила очередь, она будет пуста.  
  
## <a name="see-also"></a>См. также:  
 [Пример настраиваемого рабочего процесса &#40;Master Data Services&#41;](create-a-custom-workflow-example.md)   
 [Описание XML настраиваемого рабочего процесса (службы Master Data Services)](create-a-custom-workflow-xml-description.md)  
  
  
