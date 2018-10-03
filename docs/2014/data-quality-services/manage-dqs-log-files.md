---
title: Управление файлами журнала DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- logging
- log files
- dqs log files
ms.assetid: 4fccfd24-aede-4882-be69-ec1e82682e16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 48a1dd98c92d7faabb97033359d01f211fb5c0ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056051"
---
# <a name="manage-dqs-log-files"></a>Управление файлами журнала DQS
  Файлы журнала[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) полезны при диагностике и устранении проблем в [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]и [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]. Отдельные файлы журнала создаются для [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]и [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].  
  
 С помощью [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] вы можете настроить параметр серьезности для записи в журнал для функций и модулей [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . Кроме того, вы можете настроить некоторые другие (дополнительные) параметры для файлов журналов DQS, вручную изменив параметры конфигурации для журнала DQS в базе данных DQS_MAIN и XML-файле на компьютере [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] .  
  
##  <a name="DQSServer"></a> Файл журнала сервера DQS  
 Файл журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , DQServerLog.DQS_MAIN.log, содержит журналы видов деятельности, которые запускаются на сервере [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]. Если был установлен экземпляр SQL Server по умолчанию, файл DQServerLog.DQS_MAIN.log находится в папке «C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log». Файл журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] содержит следующие элементы данных, разделенные знаком вертикальной черты (|):  
  
-   Дата и время  
  
-   Имя потока  
  
-   Идентификатор потока  
  
-   Серьезность сведений в журнале («Предупреждение», «Ошибка», «Неустранимая ошибка», «Сведения» и «Отладка»)  
  
    > [!NOTE]  
    >  Серьезность сведений в журнале «Отладка» — такая же, как «Подробные».  
  
-   UID (идентификатор внутренней инфраструктуры DQS)  
  
-   Пространство имен  
  
-   Класс и метод  
  
-   Сообщение  
  
 Наряду с этим файл журнала отображает сведения о версии приложения, имени компьютера, имени пользователя и операционной системе.  
  
 Образец записи в файле журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] выглядит так:  
  
```  
23-08-2013 01:45:29|[]|4|INFO|PUID|InfInfoModuleStarting|Microsoft.Ssdqs.Core.Startup.ServerInit|Starting DQS ServerInit: version [12.0.0.0], machine name [DQS-TEST], user name [NT Service\MSSQLSERVER], operating system [Microsoft Windows NT 6.1.7600.0]...  
```  
  
 Файл DQServerLog.DQS_MAIN.log — последовательно обновляемый, и новый файл журнала создается после того, как размер существующего файла превышает предел, указанный в параметрах конфигурации журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . Дополнительные сведения см. в разделе [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).  
  
##  <a name="DQSClient"></a> Файл журнала клиента DQS  
 Файл журнала [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , DQClientLog.log, включает журналы на клиентской стороне. Файл журнала [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] находится в папке % APPDATA%\SSDQS\Log. Файл журнала [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] содержит такой же набор сведений, как файл журнала сервера, но на клиентской стороне.  
  
 Как и файл журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , файл журнала [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , также последовательно обновляемый, и новый файл журнала создаются после того, как размер существующего файла превышает предел, указанный в параметрах конфигурации журнала [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Дополнительные сведения см. в разделе [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).  
  
##  <a name="DQSCleansing"></a> Файл журнала компонента очистки DQS  
 Файл журнала [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] , DQSSSISLog.log, включает журналы действий, выполненных с использованием [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]. Файл журнала компонента [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] находится в папке % APPDATA%\SSDQS\Log. Файл журнала [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] содержит такой же набор сведений, как файл журнала сервера, но для [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].  
  
##  <a name="RT"></a> Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Инструкции по настройке параметров серьезности записи в журнал для файлов журнала DQS с помощью [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].|[Настройка степеней серьезности для файлов журнала DQS](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|Инструкции по ручной настройке дополнительных параметров для файлов журнала DQS.|[Настройка дополнительных параметров для файлов журнала DQS](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
  
## <a name="see-also"></a>См. также  
 [Администрирование DQS](../../2014/data-quality-services/dqs-administration.md)  
  
  
