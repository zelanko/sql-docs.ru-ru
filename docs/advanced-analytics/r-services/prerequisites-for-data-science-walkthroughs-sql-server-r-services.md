---
title: "Предварительные требования для работы с пошаговыми руководствами по обработке и анализу данных (службы SQL Server R Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 0b0582b8-8843-4787-94a8-2e28bdc04fb2
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Предварительные требования для работы с пошаговыми руководствами по обработке и анализу данных (службы SQL Server R Services)
Работать с пошаговыми руководствами рекомендуется на рабочей станции R, которая может подключаться к серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в той же сети. Работать с пошаговым руководством можно также на компьютере, на котором установлены как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и среда разработки R. 
  
  
## <a name="install-sql-server-2016-r-services-in-database"></a>Установка служб SQL Server 2016 R Services (в базе данных)  
У вас должен быть доступ к экземпляру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  с установленными службами [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] . Дополнительные сведения об установке служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]см. в разделе [Установка служб SQL Server R Services (в базе данных)](https://msdn.microsoft.com/library/mt696069.aspx).  
  
  
> [!IMPORTANT]  
> Обязательно используйте [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или более поздней версии. Предыдущие версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживают интеграцию с R, но вы можете использовать предыдущие версии баз данных SQL в качестве источника данных ODBC.  
  
## <a name="install-an-r-development-environment"></a>Установка среды разработки R  
Для выполнения этого пошагового руководства на компьютере требуется среда разработки R или любая другая программа командной строки, позволяющая выполнять команды R.    
  
- **Средства R для Visual Studio** — это бесплатный подключаемый модуль, предоставляющий возможности Intellisense, отладки и поддержки Microsoft R Server и служб SQL Server R Services. Чтобы скачать эти средства, перейдите на страницу [Средства R для Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx).  
    
- **Клиент Microsoft R** — это упрощенное средство разработки, которое поддерживает разработку на языке R с использованием пакетов ScaleR. Чтобы получить его, см. статью о [начале работы с клиентом Microsoft R](https://msdn.microsoft.com/microsoft-r/r-client-get-started).
  
- **RStudio** — одна из наиболее популярных сред для разработки на языке R. Дополнительные сведения см. на странице [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/).  
  
    Однако это руководство нельзя пройти с помощью универсальной установки RStudio или другой среды. Также необходимо установить пакеты R и библиотеки подключений для Microsoft R Open. Дополнительные сведения см. в разделе [Настройка клиента обработки и анализа данных](https://msdn.microsoft.com/library/mt696067.aspx).  

- Средства R (R.exe, RTerm.exe, RScripts.exe) устанавливаются по умолчанию при установке [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]. Если вы не хотите устанавливать интегрированную среду разработки, вы можете использовать эти средства.  
  
  
## <a name="get-permissions-to-connect-to-sql-server"></a>Получение разрешений на подключение к SQL Server  
В этом пошаговом руководстве вы подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения скриптов и отправки данных. Для этого требуется допустимое имя входа на сервере базы данных.  Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Попросите администратора базы данных создать для вас учетную запись на сервере со следующими правами в базе данных, в которой будет использоваться R:  
  
-   создание базы данных, таблиц, функций и хранимых процедур;    
-   вставка данных в таблицу.  
  
  
## <a name="start-the-walkthrough"></a>Начало выполнения пошагового руководства  
[Занятие 1. Подготовка данных (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
