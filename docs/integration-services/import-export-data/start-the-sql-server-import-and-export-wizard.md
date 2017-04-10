---
title: "Start the SQL Server Import and Export Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "мастер импорта и экспорта SQL Server"
  - "запуск мастера импорта и экспорта SQL Server"
  - "мастер импорта и экспорта"
  - "запуск мастера импорта и экспорта данных"
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
caps.latest.revision: 130
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 112
---
# Start the SQL Server Import and Export Wizard
Мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно запустить одним из следующих способов.
-   Из [меню "Пуск"](#startStart) или [командной строки](#startCmd), чтобы импортировать данные из любого из поддерживаемых источников данных или экспортировать данные в них.
-   Из [SQL Server Management Studio (SSMS)](#startSSMS), если импорт или экспорт выполняется для SQL Server.
-   Из [Visual Studio c SQL Server Data Tools (SSDT)](#startVS), если у вас открыт проект SQL Server Integration Services.

В этом разделе описывается только **запуск** мастера.
-   Обзор мастера см. в статье [Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).
-   Если вам нужна информация о процедурах, выполняемых в мастере, выберите нужную страницу в меню навигации по контенту. Каждой странице мастера соответствует отдельная страница документации. Вы можете также нажать клавишу F1 при просмотре любой страницы или диалогового окна, чтобы открыть документацию по текущей странице мастера.

**Запустите мастер.** Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName] (../Token/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).  

## <a name="a-namestartstarta-start-the-wizard-from-the-start-menu"></a><a name="startStart"></a> Запуск мастера из меню "Пуск"  
1.  В меню **Пуск** выберите пункт **Все программы**.
2.  Найдите и разверните **Microsoft SQL Server 2016**.
3.  Выберите один из следующих параметров:
  
    -   **Импорт и экспорт данных SQL Server 2016 (64-разрядная версия)**
          
    -   **Импорт и экспорт данных SQL Server 2016 (32-разрядная версия)**  
  
Если источнику данных не требуется 32-разрядный поставщик данных, выбирайте 64-разрядную версию мастера.
 
![Запуск мастера из окна "Пуск"](../../integration-services/import-export-data/media/start-wizard-start.jpg)
  
## <a name="a-namestartcmda-start-the-wizard-from-the-command-prompt"></a><a name="startCmd"></a> Запуск мастера из командной строки  
В окне командной строки запустите **DTSWizard.exe** в одном из следующих каталогов:  
  
-   **C:\Program Files\Microsoft SQL Server\130\DTS\Binn** для 64-разрядной версии.  
  
-   **C:\Program Files (x86)\Microsoft SQL Server\130\DTS\Binn** для 32-разрядной версии.  
  
Если источнику данных не требуется 32-разрядный поставщик данных, выбирайте 64-разрядную версию мастера.

![Запуск мастера из командной строки](../../integration-services/import-export-data/media/start-wizard-cmd.jpg)  
  
## <a name="a-namestartssmsa-start-the-wizard-from-sql-server-management-studio-ssms"></a><a name="startSSMS"></a> Запуск мастера в среде SQL Server Management Studio (SSMS)  
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].
2.  Разверните узел **Базы данных**.
3.  Щелкните базу данных правой кнопкой мыши.
4.  Наведите указатель мыши на пункт **Задачи**.
5.  Выберите один из следующих параметров:
  
    -   **Импорт данных**
      
    -   **Экспорт данных**  

![Запуск мастера SSMS](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

Если у вас не установлен SQL Server или SQL Server есть, но нет SQL Server Management Studio, см. статью [Скачивание SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
    
## <a name="a-namestartvsa-start-the-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a><a name="startVS"></a> Запуск мастера из Visual Studio c SQL Server Data Tools (SSDT)  
 В Visual Studio с [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] откройте проект Integration Services и выполните одно из описанных ниже действий.  
  
-   В меню **Проект** выберите пункт **Мастер импорта и экспорта служб SSIS**. 

    ![Запуск мастера из меню "Проект"](../../integration-services/import-export-data/media/start-wizard-project.jpg) 
    
    \-или -
    
-   В обозревателе решений щелкните правой кнопкой мыши папку **Пакеты служб SSIS** и выберите **Мастер импорта и экспорта служб SSIS**.

    ![Запуск мастера из папки "Пакеты"](../../integration-services/import-export-data/media/start-wizard-packages.jpg)

Если среда Visual Studio не установлена или установлена без SQL Server Data Tools, см. статью [Скачать SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx). 

## <a name="get-help-while-the-wizard-is-running"></a>Получение справки во время работы мастера
> [!TIP] Нажмите клавишу F1 при просмотре любой страницы или диалогового окна, чтобы открыть документацию по текущей странице мастера.   

 ## <a name="whats-next"></a>Дальнейшие действия  
 При запуске мастера открывается страница **Мастер импорта и экспорта SQL Server**. На этой странице никакие действия не требуются. Дополнительные сведения см. в разделе [Мастер импорта и экспорта SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
  