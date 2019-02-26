---
title: Запуск мастера импорта и экспорта SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 06/20/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8db11de67db871df75605099191a2ae0e34be0b9
ms.sourcegitcommit: a13256f484eee2f52c812646cc989eb0ce6cf6aa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2019
ms.locfileid: "56801338"
---
# <a name="start-the-sql-server-import-and-export-wizard"></a>запустить мастер импорта и экспорта SQL Server


Запустите мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] одним из описанных здесь способов, чтобы импортировать данных из любого поддерживаемого источника данных и экспортировать данные в него.

> [!IMPORTANT]
> В этом разделе описывается только **запуск** мастера. Если вам нужны другие сведения, см. раздел [Связанные задачи и содержимое](#related).

Варианты запуска мастера:
-   Из [меню "Пуск"](#startStart).
-   Из [командной строки](#startCmd). 
-   Из [SQL Server Management Studio (SSMS)](#startSSMS).
-   Из [Visual Studio c SQL Server Data Tools (SSDT)](#startVS).

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Предварительное требование — у вас на компьютере установлен этот мастер?
Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

> [!NOTE]
> Чтобы использовать 64-разрядную версию мастера экспорта и импорта SQL Server, нужно установить SQL Server. SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS) являются 32-разрядными приложениями и устанавливают только 32-разрядные файлы, включая 32-разрядную версию мастера.

## <a name="startStart"></a> меню "Пуск"  
### <a name="start-the-sql-server-import-and-export-wizard-from-the-start-menu"></a>Запуск мастера экспорта и импорта SQL Server из меню "Пуск"
1.  В меню **Пуск** найдите и разверните узел **Microsoft SQL Server 2016**.
3.  Выберите один из следующих параметров:
  
    -   **Импорт и экспорт данных SQL Server 2016 (64-разрядная версия)**
          
    -   **Импорт и экспорт данных SQL Server 2016 (32-разрядная версия)**  
  
    Если источнику данных не требуется 32-разрядный поставщик данных, выбирайте 64-разрядную версию мастера.
 
    ![Запуск мастера из окна "Пуск"](../../integration-services/import-export-data/media/start-wizard-start.jpg)
  
## <a name="startCmd"></a> Command prompt
### <a name="start-the-sql-server-import-and-export-wizard-from-the-command-prompt"></a>Запуск мастера экспорта и импорта SQL Server из командной строки  
В окне командной строки запустите **DTSWizard.exe** в одном из следующих каталогов:  
  
-   **C:\Program Files\Microsoft SQL Server\130\DTS\Binn** для 64-разрядной версии.  
  
-   **C:\Program Files (x86)\Microsoft SQL Server\130\DTS\Binn** для 32-разрядной версии.  
  
Если источнику данных не требуется 32-разрядный поставщик данных, выбирайте 64-разрядную версию мастера.

![Запуск мастера из командной строки](../../integration-services/import-export-data/media/start-wizard-cmd.jpg)  
  
## <a name="startSSMS"></a> SQL Server Management Studio (SSMS)
### <a name="start-the-sql-server-import-and-export-wizard-from-sql-server-management-studio-ssms"></a>Запуск мастера экспорта и импорта SQL Server из среды SQL Server Management Studio (SSMS)    
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].
    
2.  Разверните узел **Базы данных**.
3.  Щелкните базу данных правой кнопкой мыши.
4.  Наведите указатель мыши на пункт **Задачи**.
5.  Выберите один из следующих параметров:
  
    -   **Импорт данных**
      
    -   **Экспорт данных**  

    ![Запуск мастера SSMS](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

Если у вас не установлен SQL Server или SQL Server есть, но нет SQL Server Management Studio, см. статью [Скачивание SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).
  
## <a name="startVS"></a> Visual Studio
### <a name="start-the-sql-server-import-and-export-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a>Запуск мастера экспорта и импорта SQL Server из Visual Studio c SQL Server Data Tools (SSDT) 
 В Visual Studio с [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект Integration Services и выполните одно из описанных ниже действий. 
  
-   В меню **Проект** выберите пункт **Мастер импорта и экспорта служб SSIS**. 

    ![Запуск мастера из меню "Проект"](../../integration-services/import-export-data/media/start-wizard-project.jpg) 
    
    \-или -
    
-   В обозревателе решений щелкните правой кнопкой мыши папку **Пакеты служб SSIS** и выберите **Мастер импорта и экспорта служб SSIS**.

    ![Запуск мастера из папки "Пакеты"](../../integration-services/import-export-data/media/start-wizard-packages.jpg)

Если среда Visual Studio не установлена или установлена без SQL Server Data Tools, см. статью [Скачать SQL Server Data Tools (SSDT)](../../ssdt/download-sql-server-data-tools-ssdt.md).

## <a name="get-the-wizard"></a>Получение мастера
Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="get-help-while-the-wizard-is-running"></a>Получение справки во время работы мастера
> [!TIP]
> Нажмите клавишу F1 при просмотре любой страницы или диалогового окна, чтобы открыть документацию по текущей странице мастера.   

 ## <a name="whats-next"></a>Дальнейшие действия  
 При запуске мастера открывается страница **Мастер импорта и экспорта SQL Server**. На этой странице никакие действия не требуются. Дополнительные сведения см. в разделе [Мастер импорта и экспорта SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
## <a name="related"></a> Связанные задачи и содержимое  
 Ниже приведены некоторые основные задачи.
-   **См. краткий пример работы мастера.**

    -   **Ознакомьтесь со снимками экрана.** Просмотрите простой полный пример в разделе [Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

    -   **Посмотрите видео.** В этом четырехминутном видео на YouTube демонстрируется работа мастера и объясняется, как с его помощью экспортировать данные в Excel: [Использование мастера импорта и экспорта SQL Server для экспорта в Excel](https://go.microsoft.com/fwlink/?linkid=829049).

-   **Дополнительные сведения о работе мастера.**

    -   **Дополнительные сведения о мастере.** Обзор мастера см. в статье [Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

    -   **Дополнительные сведения о шагах в мастере.** Если вам нужны сведения о шагах, выполняемых в мастере, см. в разделе [Шаги в мастере импорта и экспорта SQL Server](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Каждой странице мастера соответствует отдельная страница документации.

    -   **Сведения о подключении к источникам данных и назначениям.** Сведения о подключении к данным см. на соответствующей странице, выбрав ее в списке в разделе [Подключение к источникам данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Для каждого распространенного источника данных имеется отдельная страница документации.


