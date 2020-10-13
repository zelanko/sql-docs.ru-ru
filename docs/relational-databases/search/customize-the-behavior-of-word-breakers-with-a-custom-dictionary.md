---
description: Настройка поведения средств разбиения текста на слова с помощью пользовательского словаря (поиск в SQL Server)
title: Настройка поведения средств разбиения текста на слова с помощью пользовательского словаря
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.custom: seo-lt-2019
ms.openlocfilehash: 46fb0f6fa4e8607296ead7a2f5e77ac97e75f9d5
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866988"
---
# <a name="customize-behavior-of-word-breakers-with-a-custom-dictionary-sql-server-search"></a>Настройка поведения средств разбиения текста на слова с помощью пользовательского словаря (поиск в SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Можно настроить работу средства разбиения по словам для определенного языка, создав для этого языка собственный файл словаря. Например, можно запретить средству разбиения по словам разбивать определенные термины или фразы.  
  
 Дополнительные сведения см. в следующей статье SharePoint:  
  
 [Создание пользовательского словаря (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc263242(v=office.14))  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]файл пользовательского словаря должен быть размещен в следующей папке:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 После создания или изменения собственных файлов словарей перезапустите средство запуска управляющей программы полнотекстовой фильтрации SQL Server следующей командой:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
