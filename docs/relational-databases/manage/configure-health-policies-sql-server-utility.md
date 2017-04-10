---
title: "Настройка политик исправности (служебная программа SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Настройка политик исправности (служебная программа SQL Server)
  Панель мониторинга программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет просмотреть параметры программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложений уровня данных. Дополнительные сведения см. в разделе [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Чтобы просмотреть результаты политики исправности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], подключитесь к точке управления служебной программой из среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в статье [Использование проводника служебных программ для управления служебной программой SQL Server](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Политики исправности программы можно настроить для приложений уровня данных и экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] политика исправности может быть задана глобально для всех приложений уровня данных и управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], либо ее можно задать индивидуально для отдельных приложений уровня данных и управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Политики наблюдения для приложений уровня данных  
 Политики чрезмерного и недостаточного использования для приложений уровня данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Загрузка процессора приложением уровня данных.  
  
-   Файловое пространство приложения уровня данных для файлов баз данных.  
  
-   Файловое пространство приложения уровня данных для томов хранилища.  
  
-   Использование процессора компьютера.  
  
> [!NOTE]  
>  Для приложений уровня данных использование томов хранилища и процессора является политиками только для чтения.  
  
 Дополнительные сведения о просмотре или изменении глобальных политик наблюдения для приложений уровня данных см. в статье [Администрирование программ (служебная программа SQL Server)](../Topic/Utility%20Administration%20\(SQL%20Server%20Utility\).md).  
  
 Дополнительные сведения о просмотре и изменении политик наблюдения для отдельных приложений уровня данных см. в статье [Подробные сведения о развернутом приложении уровня данных (служебная программа SQL Server)](../Topic/Deployed%20Data-tier%20Application%20Details%20\(SQL%20Server%20Utility\).md).  
  
## Политики наблюдения для управляемых экземпляров SQL Server  
 Политики чрезмерного и недостаточного использования для управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для файлов баз данных.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для томов хранилища.  
  
-   Использование процессора компьютера.  
  
 Дополнительные сведения о просмотре или изменении глобальных политик наблюдения для управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Администрирование программ (служебная программа SQL Server)](../Topic/Utility%20Administration%20\(SQL%20Server%20Utility\).md).  
  
 Дополнительные сведения о просмотре и изменении политик наблюдения для отдельных управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Подробные сведения о развернутом приложении уровня данных (служебная программа SQL Server)](../Topic/Managed%20Instance%20Details%20\(SQL%20Server%20Utility\).md).  
  
## См. также:  
 [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Уменьшение уровня шума в политиках загрузки ЦП (служебная программа SQL Server)](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  