---
title: "Создание настраиваемого рабочего процесса (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 8e4403e9-595c-4b6b-9d0c-f6ae1b2bc99d
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dacc515af7f4d05fc2bad2fd43535bc27c13ea76
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

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
 Пользовательский рабочий процесс представляет собой сборку библиотеки классов .NET, которая реализует интерфейс <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. Служба SQL Server MDS Workflow Integration Service обращается к методу <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> для выполнения кода. Пример кода, который реализует <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>, в разделе [пользовательского рабочего процесса примера &#40; Службы Master Data Services &#41; ](../../master-data-services/develop/create-a-custom-workflow-example.md).  
  
 Выполните следующие действия, чтобы создать с помощью Visual Studio 2010 сборку, которую сможет вызывать служба SQL Server MDS Workflow Integration Service для обработки пользовательского рабочего процесса:  
  
1.  В Visual Studio 2010, создайте новый **библиотеки классов** проекта, который будет использован язык, по своему усмотрению. Чтобы создать библиотеку классов C#, выберите **Visual C# \Windows** типы проектов и выберите **библиотеки классов** шаблона. Введите имя для проекта, такие как **MDSWorkflowTest**и нажмите кнопку **ОК**.  
  
2.  Добавьте ссылку на файл Microsoft.MasterDataServices.WorkflowTypeExtender.dll. Эту сборку можно найти в \<установочная папка > \Master Data Services\WebApplication\bin.  
  
3.  Добавьте строку «using Microsoft.MasterDataServices.Core.Workflow;» в файл с кодом C#.  
  
4.  В объявлении класса установите наследование от <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. Объявление класса должно выглядеть примерно так: «public class WorkflowTester : IWorkflowTypeExtender».  
  
5.  Реализуйте интерфейс <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. Метод <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> вызывается службами SQL Server MDS Workflow Integration Service для запуска рабочего процесса.  
  
6.  Скопируйте сборку в расположение SQL Server MDS Workflow Integration Service исполняемый файл с именем Microsoft.MasterDataServices.Workflow.exe, в \<установочная папка > \Master Data Services\WebApplication\bin.  
  
### <a name="configure-sql-server-mds-workflow-integration-service"></a>Настройка службы Configure SQL Server MDS Workflow Integration Service  
 Измените файл конфигурации [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], включив в него данные соединения для базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], и свяжите тег со сборкой обработчика рабочих процессов, выполнив следующие действия.  
  
1.  Найдите файл Microsoft.MasterDataServices.Workflow.exe.config в \<установочная папка > \Master Data Services\WebApplication\bin.  
  
2.  Добавьте данные соединения с базой данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в параметр «ConnectionString». Если в установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются параметры сортировки, учитывающие регистр, то имя базы данных следует ввести в том же регистре, который используется в базе данных. Например, полный тег параметра может выглядеть следующим образом:  
  
    ```xml  
    <setting name="ConnectionString" serializeAs="String">  
        <value>Server=myServer;Database=myDatabase;Integrated Security=True</value>  
    </setting>  
    ```  
  
3.  Под параметром «ConnectionString» добавьте параметр «WorkflowTypeExtenders», чтобы связать имя тега с используемой сборкой обработчика рабочих процессов. Например:  
  
    ```xml  
    <setting name="WorkflowTypeExtenders" serializeAs="String">  
        <value>TEST=MDSWorkflowTestLib.WorkflowTester, MDSWorkflowTestLib</value>  
    </setting>  
    ```  
  
     Внутренний текст \<значение > тег — в виде \<тег рабочего процесса > =\<имя типа с указанием сборки рабочего процесса >. \<Тег рабочего процесса > — это имя используется для определения сборки обработчика рабочего процесса при создании бизнес-правила в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. \<Имя типа с указанием сборки рабочего процесса > является пространством имен, имя класса рабочего процесса, используя запятую, за которым следует отображаемое имя сборки. Если сборка имеет строгое имя, то также необходимо указать данные о версии и ее PublicKeyToken. Может включать несколько \<параметр > теги, если вы создали несколько обработчиков рабочих процессов для различных типов рабочих процессов.  
  
> [!NOTE]  
>  В зависимости от конфигурации сервера при попытке сохранить файл Microsoft.MasterDataServices.Workflow.exe.config на экране может появиться сообщение об ошибке «В доступе отказано». В этом случае временно отключите контроль учетных записей на сервере. Чтобы сделать это, откройте панель управления, нажмите кнопку **система и безопасность**. В разделе **центр поддержки**, нажмите кнопку **параметры контроля учетных записей пользователя изменить**. В **параметры контроля учетных записей пользователя** диалоговое окно, переместите ползунок вниз, чтобы не получать никаких уведомлений. Перезагрузите компьютер и повторите описанные ранее действия для изменения файла конфигурации. После сохранения файла, сбросьте параметры контроля учетных записей пользователей на значения по умолчанию.  
  
### <a name="start-sql-server-mds-workflow-integration-service"></a>Запуск службы SQL Server MDS Workflow Integration Service  
 По умолчанию служба SQL Server MDS Workflow Integration Service не установлена. Чтобы использовать эту службу, ее сначала необходимо установить. Для обеспечения наибольшей безопасности создайте локального пользователя для этой службы и предоставьте этому пользователю только те разрешения, которые необходимы для выполнения операций рабочего процесса. Чтобы создать пользователя, установите службу, запустите ее и выполните следующие действия.  
  
1.  С помощью диспетчера локальных пользователей и групп создайте локального пользователя с именем, например, mds_workflow_service.  
  
2.  С помощью среды SQL Server Management Studio предоставьте пользователю mds_workflow_service разрешение на выполнение хранимой процедуры [mdm].[udpExternalActionsGet]. Для этого создайте новое имя входа для учетной записи mds_workflow_service, создайте нового пользователя в базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], сопоставьте этого пользователя с именем входа mds_workflow_service и предоставьте ему разрешение EXECUTE для хранимой процедуры [mdm].[udpExternalActionsGet].  
  
3.  Предоставьте пользователю mds_workflow_service разрешение на выполнение сборки обработчика рабочих процессов. Чтобы сделать это, добавьте пользователя службы mds_workflow_service на **безопасности** вкладке **свойства** рабочего процесса сборки обработчика и предоставьте пользователю разрешение READ и EXECUTE.  
  
4.  Предоставьте пользователю службы mds_workflow_service разрешение на выполнение исполняемого файла службы SQL Server MDS Workflow Integration Service. Чтобы сделать это, добавьте пользователя службы mds_workflow_service на **безопасности** вкладке **свойства** из Microsoft.MasterDataServices.Workflow.exe в \<установочная папка > \Master Data Services\WebApplication\bin и предоставьте пользователю разрешение READ и EXECUTE.  
  
5.  Установите службу SQL Server MDS Workflow Integration Service с помощью программы установки .NET с именем InstallUtil.exe. InstallUtil.exe можно найти в папке установки .NET, например C:\Windows\Microsoft.NET\Framework\v4.0.30319\\. Установите службу SQL Server MDS Workflow Integration Service, введя в командной строке следующую команду:  
  
    ```  
    C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil Microsoft.MasterDataServices.Workflow.exe  
    ```  
  
     При запросе во время установки укажите пользователя mds_workflow_service.  
  
6.  Запустите службу SQL Server MDS Workflow Integration Service с помощью оснастки «Службы». Для этого найдите SQL Server MDS Workflow Integration Service в оснастке служб, выберите его и нажмите кнопку **запустить** ссылку.  
  
### <a name="create-a-workflow-business-rule"></a>Создание бизнес-правила рабочего процесса  
 С помощью веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] создайте и опубликуйте бизнес-правило, которое при его применении будет запускать рабочий процесс. Бизнес-правило должно содержать действия, которые изменяют значения атрибутов таким образом, чтобы после его применения правило не могло быть применено еще раз. Например, критерии бизнес-правила должны быть соблюдены, когда значение атрибута «Price» больше 500, а значение атрибута «Approved» не задано. В этом случае правило должно включать два действия: задание значения «Pending» атрибуту «Approved» и запуск рабочего процесса. Также можно создать правило, в котором будет использоваться условие «изменилось», и добавить атрибуты в группы отслеживания изменений. Дополнительные сведения о бизнес-правилах см. в разделе [бизнес-правила &#40; Службы Master Data Services &#41; ](../../master-data-services/business-rules-master-data-services.md).  
  
 Создайте бизнес-правило, которое будет запускать пользовательский рабочий процесс в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], выполнив следующие действия.  
  
1.  В редакторе правил бизнеса из [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], после указания условий бизнес-правила, перетащите **запустить рабочий процесс** действия из **внешние действия** список **ЗАТЕМ** панели **действия** метки.  
  
2.  В **изменить действие** области в **тип рабочего процесса** введите тег, который обозначает сборку обработчика рабочего процесса. Это тег, который был задан в файле конфигурации сборки, например, TEST.  
  
3.  При необходимости установите **включать данные-член** флажок. Этот параметр устанавливается для того, чтобы включать имена атрибутов и значения из XML-файла, который передается обработчику рабочего процесса.  
  
4.  В **рабочего процесса сайта** введите имя веб-сайта. Для пользовательского рабочего процесса это может и не применяться, но может быть использовано для формирования дополнительного контекста.  
  
5.  В **имя рабочего процесса** введите имя рабочего процесса из Visual Studio. Для пользовательского рабочего процесса это может и не применяться, но может быть использовано для формирования дополнительного контекста.  
  
6.  Сохраните и опубликуйте бизнес-правило.  
  
### <a name="apply-business-rules-to-start-a-workflow"></a>Применение бизнес-правила к запуску рабочего процесса  
 Примените бизнес-правило к данным, чтобы запустить рабочий процесс. Для этого с помощью веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] измените запись, содержащую элементы, которые требуется проверить. Нажмите кнопку **применение бизнес-правил**. В ответ на бизнес-правило веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] заполняет очередь компонента Service Broker базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Когда служба SQL Server MDS Workflow Integration Service проверяет очередь, она отправляет данные указанной сборке обработчика рабочего процесса и очищает очередь. Сборка обработчика рабочего процесса выполняет те действия, которые были запрограммированы.  
  
## <a name="troubleshoot-custom-workflows"></a>Устранение неполадок пользовательских рабочих процессов  
 Если сборка обработчика рабочего процесса не получает данные, можно попробовать выполнить отладку службы SQL Server MDS Workflow Integration Service или просмотреть очередь компонента Service Broker.  
  
### <a name="debug-sql-server-mds-workflow-integration-service"></a>Отладка службы SQL Server MDS Workflow Integration Service  
 Для отладки службы SQL Server Workflow Integration Service выполните следующие действия.  
  
1.  С помощью оснастки «Службы» остановите службу.  
  
2.  Откройте командную строку, перейдите в каталог, в котором находится служба и запустите службу в пультовом режиме, введя следующую команду: Microsoft.MasterDataServices.Workflow.exe -console.  
  
3.  В веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] обновите элемент и примените бизнес-правило еще раз. В окне консоли будут отображены подробные записи журнала.  
  
### <a name="view-the-service-broker-queue"></a>Просмотр очереди компонента Service Broker  
 Очередь компонента Service Broker, в которой содержатся основные данные, переданные в рамках рабочего процесса, находится по адресу mdm.microsoft/mdm/queue/externalaction. Очереди могут находиться в **обозревателя объектов** среды SQL Management Studio в узле компонента Service Broker [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] базы данных. Имейте в виду, что если служба должным образом очистила очередь, она будет пуста.  
  
## <a name="see-also"></a>См. также:  
 [Пример настраиваемого рабочего процесса &#40; Службы Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-example.md)   
 [Описание XML настраиваемого рабочего процесса &#40; Службы Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-xml-description.md)  
  
  
