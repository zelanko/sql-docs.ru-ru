---
title: Экспорт и импорт баз знаний DQS с помощью DQSInstaller.exe | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8234c63b-a018-4e55-8184-9a6bdf03274d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 79adb6a32992aa9a60b01a00b065c0e2c4c11440
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65487549"
---
# <a name="export-and-import-dqs-knowledge-bases-using-dqsinstallerexe"></a>Export and Import DQS Knowledge Bases Using DQSInstaller.exe

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Для существующей установки DQS все базы знаний на сервере [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] вы можете экспортировать в файл резервной копии DQS (DQSB) одновременно, а затем использовать файл DQSB для одновременного импорта всех баз знаний на другой сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] посредством запуска файла DQSInstaller.exe из командной строки. Дополнительные сведения о запуске DQSInstaller.exe из командной строки см. в подразделе [Запуск DQSInstaller.exe из командной строки](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) раздела [Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
 Эта функция позволяет создать резервную копию *всех* баз знаний на сервере [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] одновременно без необходимости экспортировать каждую из баз знаний в DQS-файл по отдельности с помощью [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]. Аналогичным образом вы можете импортировать *все* базы знаний из файла резервной копии на другой сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] одновременно, не импортируя каждую из баз знаний по отдельности из DQS-файла с помощью [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]. Это особенно полезно при создании и восстановлении резервных копий баз знаний, когда выполняется удаление сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] на одном компьютере и его повторная установка на другом компьютере. Все базы знаний в существующей установке [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] несложно экспортировать в файл резервной копии DQS (.dqsb), а затем импортировать все базы знаний из файла резервной копии после установки [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] на другом компьютере.  
  
##  <a name="export"></a> Экспорт баз знаний в DQSB-файл  
 Все базы знаний из существующего сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] вы можете экспортировать в любое время, в том числе и при удалении [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].  
  
-   Для экспорта всех баз знаний на сервере [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] в файл резервной копии DQS (.dqsb) запустите программу DQSInstaller.exe с параметром `exportkbs` из командной строки, введя полный путь к файлу и имя файла, в который будут экспортированы базы знаний. Например, для экспорта всех баз знаний в файл DQSBackup.dqsb на диске C: выполните следующую команду:  
  
    ```  
    dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  Если файл с указанным именем уже существует в заданном расположении, установщик запрашивает разрешения на то, перезаписать ли файл.  
  
-   Для экспорта всех баз знаний в файл резервной копии DQS при удалении [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]запустите программу DQSInstaller.exe с параметром `uninstall` из командной строки, задав полный путь к файлу и имя файла, в который следует экспортировать базы знаний. Например, для экспорта всех баз знаний в файл DQSBackup.dqsb на диске C: и последующего удаления [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]выполните следующую команду:  
  
    ```  
    dqsinstaller.exe -uninstall c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  Если при удалении [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] в параметре командой строки `uninstall` не будут указаны полные путь к файлу и имя файла резервной копии DQS, то отображается сообщение, которое предупреждает об удалении всех баз знаний и позволяет определить, продолжить ли процесс удаления.  
  
##  <a name="import"></a> Импорт баз знаний из DQSB-файла  
 После завершения установки [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] вы можете импортировать все базы знаний из файла резервной копии DQS (.dqsb). Для импорта баз знаний необходим допустимый файл резервной копии DQS (.dqsb).  
  
 Запустите программу DQSInstaller.exe с параметром `importkbs` из командной строки, задав полный путь к файлу и имя файла, из которого следует импортировать базы знаний. Например, для импорта всех баз знаний из файла DQSBackup.dqsb на диске C: выполните следующую команду:  
  
```  
dqsinstaller.exe -importkbs c:\DQSBackup.dqsb  
```  
  
 Если в [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] имеются существующие базы знаний с теми же именами, что и у импортируемых баз данных, к именам импортируемых баз данных будет добавлен символ подчеркивания (_) и целочисленное значение, отсчитываемое от единицы. Например, если повторяется домен "CompanyName", то импортируемый домен получит имя "CompanyName_1".  
  
## <a name="see-also"></a>См. также:  
 [Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)   
 [Установка служб Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Экспорт базы знаний в файл .dqs](../../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)   
 [Импорт базы знаний из файла .dqs](../../data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)  
  
  
