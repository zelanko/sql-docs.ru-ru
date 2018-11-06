---
title: Настройка поведения средств разбиения текста на слова с помощью пользовательского словаря | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1fd6c83e02b15fcf126e5b3d078237c07d758cf3
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032452"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Настройка поведения средств разбиения по словам при работе с пользовательским словарем
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Можно настроить работу средства разбиения по словам для определенного языка, создав для этого языка собственный файл словаря. Например, можно запретить средству разбиения по словам разбивать определенные термины или фразы.  
  
 Дополнительные сведения см. в следующей статье SharePoint:  
  
 [Создание пользовательского словаря (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]файл пользовательского словаря должен быть размещен в следующей папке:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 После создания или изменения собственных файлов словарей перезапустите средство запуска управляющей программы полнотекстовой фильтрации SQL Server следующей командой:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
