---
title: Настройка поведения средств разбиения текста на слова с помощью пользовательского словаря | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2f4fb4134dd17efa37a169265e53af9910a8d153
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288560"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Настройка поведения средств разбиения по словам при работе с пользовательским словарем
  Можно настроить работу средства разбиения по словам для определенного языка, создав для этого языка собственный файл словаря. Например, можно запретить средству разбиения по словам разбивать определенные термины или фразы.  
  
 Дополнительные сведения см. в следующей статье SharePoint:  
  
 [Создание пользовательского словаря (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]файл пользовательского словаря должен быть размещен в следующей папке:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 После создания или изменения собственных файлов словарей перезапустите средство запуска управляющей программы полнотекстовой фильтрации SQL Server следующей командой:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
