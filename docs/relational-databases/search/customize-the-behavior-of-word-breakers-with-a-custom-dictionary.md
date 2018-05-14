---
title: Настройка поведения средств разбиения текста на слова с помощью пользовательского словаря | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.component: search
ms.reviewer: ''
ms.suite: sql
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 18a2aba8a554d0c08cf8a09ac0b5c5260d8855c7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Настройка поведения средств разбиения по словам при работе с пользовательским словарем
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Можно настроить работу средства разбиения по словам для определенного языка, создав для этого языка собственный файл словаря. Например, можно запретить средству разбиения по словам разбивать определенные термины или фразы.  
  
 Дополнительные сведения см. в следующей статье SharePoint:  
  
 [Создание пользовательского словаря (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]файл пользовательского словаря должен быть размещен в следующей папке:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 После создания или изменения собственных файлов словарей перезапустите средство запуска управляющей программы полнотекстовой фильтрации SQL Server следующей командой:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
