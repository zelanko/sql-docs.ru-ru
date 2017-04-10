---
title: "Копирование состояния аспекта управления на основе политик в XML-файл | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "управление на основе политик, копирование состояния аспекта в XML-файл"
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Копирование состояния аспекта управления на основе политик в XML-файл
  В этом разделе описывается копирование состояния аспекта управления на основе политик в XML-файл в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Копирование состояния аспекта в XML-файл с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Для процедуры в этом разделе требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Копирование состояния аспекта в XML-файл  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], объект экземпляра, базу данных или объект базы данных и выберите команду **Аспекты**.  
  
2.  В диалоговом окне **Просмотр аспектов —***имя объекта* щелкните **Экспортировать текущее состояние как политику**.  
  
3.  Введите имя и путь к файлу в диалоговом окне **Экспортировать как политику** либо найдите файл при помощи кнопки "Обзор" (**...**) и введите имя XML-файла. Дополнительные сведения о доступных параметрах данного диалогового окна см. в разделе [Export As Policy Dialog Box](../../relational-databases/policy-based-management/export-as-policy-dialog-box.md)  
  
4.  После завершения нажмите кнопку **ОК**.  
  
  