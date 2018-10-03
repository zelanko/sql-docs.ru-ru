---
title: MSSQLSERVER_1803 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a51d34ac6937e8a1f968eed1c558618d8a556ef8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47703332"
---
# <a name="mssqlserver1803"></a>MSSQLSERVER_1803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
