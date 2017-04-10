---
title: "Настройка поведения средств разбиения по словам при работе с пользовательским словарем | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Настройка поведения средств разбиения по словам при работе с пользовательским словарем
  Можно настроить работу средства разбиения по словам для определенного языка, создав для этого языка собственный файл словаря. Например, можно запретить средству разбиения по словам разбивать определенные термины или фразы.  
  
 Дополнительные сведения см. в следующей статье SharePoint:  
  
 [Создание пользовательского словаря (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл пользовательского словаря должен быть размещен в следующей папке:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 После создания или изменения собственных файлов словарей перезапустите средство запуска управляющей программы полнотекстовой фильтрации SQL Server следующей командой:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  