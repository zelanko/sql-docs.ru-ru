---
title: MSSQLSERVER_4064 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 201098aadeb6bd091f0312532138f692ae8079b6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033240"
---
# <a name="mssqlserver_4064"></a>MSSQLSERVER_4064
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|4064|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DB_UFAIL_FATAL|  
|Текст сообщения|Невозможно открыть пользовательскую базу данных по умолчанию. Ошибка входа.|  
  
## <a name="explanation"></a>Объяснение  
 Имени входа SQL Server не удалось выполнить соединение из-за проблемы с базой данных по умолчанию. Либо указана недопустимая база данных, либо у имени входа нет разрешения CONNECT для этой базы данных.  
  
## <a name="user-action"></a>Действие пользователя  
 При помощи инструкции ALTER LOGIN измените базу данных по умолчанию для этого имени входа. Предоставьте имени входа разрешение CONNECT.  
  
  
