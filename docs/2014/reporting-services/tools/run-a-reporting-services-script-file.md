---
title: Запуск файла скрипта служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 603ca22a30c0c5ffe351db7370fc337e2e20e1cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66099838"
---
# <a name="run-a-reporting-services-script-file"></a>Запуск файла скрипта для служб Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Файлы скриптов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выполняются из командной строки с помощью среды скриптов служб (программа rs.exe). В программе rs.exe доступно множество аргументов командной строки. Дополнительные сведения о параметрах командной строки см. в разделе [Служебная программа RS.exe (службы SSRS)](rs-exe-utility-ssrs.md). Образцы скриптов см. на странице [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="sample-command-lines"></a>Образцы команд в командной строке  
  
-   Запустите файл Script.rss в среде выполнения скриптов, при этом укажите целевой сервер отчетов. По умолчанию применяется проверка подлинности Windows.  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver  
    ```  
  
-   Запустите файл Script.rss в среде выполнения скриптов, при этом задайте имя пользователя и пароль для ответа на вызовы веб-службы.  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   Запустите файл Script.rss в среде выполнения скриптов, задайте лимит времени ожидания для сервера в 30 секунд.  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   Запустите файл Script.rss в среде выполнения скриптов, при этом укажите глобальную переменную скрипта с именем *report*.  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   Запустите файл Script.rss в среде выполнения скриптов, при этом укажите, что операции веб-службы в файле скриптов должны выполняться в виде пакета.  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a>См. также  
 [Технический справочник (службы SSRS)](../technical-reference-ssrs.md)  
  
  
