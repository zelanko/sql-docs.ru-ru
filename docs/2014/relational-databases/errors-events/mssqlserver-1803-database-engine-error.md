---
title: MSSQLSERVER_1803 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a8472fe5f18515adae38725234a43c130d3108d0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415913"
---
# <a name="mssqlserver1803"></a>MSSQLSERVER_1803
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1803|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NO_SPACE|  
|Текст сообщения|Ошибка операции CREATE DATABASE. Размер первичного ключа должен быть как минимум %d МБ, чтобы вместить копию базы данных model.|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает базу данных путем копирования базы данных model. Затем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] переименовывает копию и увеличивает новую базу данных до необходимого размера. В этом случае пользователь выполняет попытку создания базы данных, размер которой меньше размера базы данных model. При выполнении операции произошла ошибка, поскольку копия базы данных model не помещалась в первичном файле данных, так как размер файла меньше размера базы данных model.  
  
## <a name="user-action"></a>Действие пользователя  
 Создайте базу данных с помощью файла базы данных большего размера. Затем при необходимости сожмите базу данных с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или инструкции DBCC SHRINKDATABASE.  
  
  
