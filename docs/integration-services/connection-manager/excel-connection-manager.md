---
title: Диспетчер подключений Excel | Документы Майкрософт
ms.date: 04/02/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9ce3042bedd23c5ee173b1df7669a09cce35351
ms.sourcegitcommit: 365a919e3f0b0c14440522e950b57a109c00a249
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75831754"
---
# <a name="excel-connection-manager"></a>Диспетчер соединений с Excel

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Диспетчер соединений Excel делает доступным соединение пакета с файлом рабочей книги [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. Источник Excel и назначение Excel, которые включены в службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], используют диспетчер подключений Excel.  
 
> [!IMPORTANT]
> Дополнительные сведения о подключении к файлам Excel, а также об ограничениях и известных проблемах, связанных с загрузкой данных в файлы этого приложения и из них, см. в разделе [Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md).

 Если происходит добавление диспетчера соединений Excel к пакету, служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер соединений, который будет разрешен как соединение Excel во время выполнения, задает свойства диспетчера соединений и добавляет диспетчер соединений к коллекции **Connections** пакета.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **EXCEL**.  
  
## <a name="configure-the-excel-connection-manager"></a>Настройка диспетчера соединений Excel  
 Чтобы настроить диспетчер соединений Excel, выполните следующее:  
  
-   Укажите путь файла рабочей книги Excel.  
  
-   Укажите версию приложения Excel, использовавшуюся при создании файла.  
  
-   Укажите, содержатся ли имена столбцов в первой строке выбранного рабочего листа или диапазона.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в разделе [Редактор диспетчера соединений с Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="excel-connection-manager-editor"></a>редактор диспетчера соединений с Excel
  Диалоговое окно **Редактор диспетчера соединений с Excel** используется для добавления подключения к существующему или новому файлу книги [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] .  
  
### <a name="options"></a>Параметры  
 **Путь к файлу Excel**  
 Введите путь и имя существующего или нового файла книги Excel.  
   
 **Обзор**  
 Для перехода в папку, в которой существует файл Excel или в которой будет создан новый файл, используйте диалоговое окно **Открыть**.  
  
 **Версия Excel**  
 Позволяет указать версию Microsoft Excel, в которой был создан файл.  
  
 **Первая строка содержит имена столбцов**  
 Позволяет указать, содержит ли первая строка данных выбранного листа имена столбцов. По умолчанию значение этого параметра равно **True**.  

## <a name="solution-to-import-data-with-mixed-data-types-from-excel"></a>Решение для импорта смешанных типов данных из Excel

Если используются данные, содержащие смешанные типы данных, то по умолчанию драйвер Excel считывает первые 8 строк (настраивается ключом реестра **TypeGuessRows**). В зависимости от первых 8 строк данных драйвер Excel пытается распознать тип данных каждого столбца. Например, если источник данных Excel содержит числа и текст в одном столбце, а первые 8 строк содержат числа, то драйвер может на основе первых 8 строк определить, что данные в столбце являются целочисленными. В этом случае службы SSIS пропускают текстовые значения и импортируют их в назначение как значения NULL.

Чтобы устранить эту проблему, можно попробовать одно из следующих решений.

* Измените тип столбца Excel на **Текстовый** в файле Excel.
* Добавьте расширенное свойство IMEX в строку подключения, чтобы переопределить поведение драйвера по умолчанию. При добавлении расширенного свойства ";IMEX=1" в конец строки подключения Excel обрабатывает все данные как текст. См. следующий пример.
    
  ```ACE OLEDB connection string:
  Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\ExcelFileName.xlsx;Extended Properties="EXCEL 12.0 XML;HDR=YES;IMEX=1";
  ```

   Для надежной работы этого решения может также потребоваться изменить параметры реестра. Файл main.cmd выглядит следующим образом:
  
   ```cmd
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\12.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\12.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\15.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   ```

* Сохраните файл в формате CSV и активируйте в пакете служб SSIS поддержку импорта CSV.

## <a name="related-tasks"></a>Связанные задачи  
[Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)  
[Источник Excel](../data-flow/excel-source.md)  
[Назначение «Excel»](../data-flow/excel-destination.md)
