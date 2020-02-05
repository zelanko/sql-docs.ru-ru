---
title: MSSQLSERVER_4064 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81537ea994fa22ee9cafb2ba031677a1d5544dcd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68123368"
---
# <a name="mssqlserver_4064"></a>MSSQLSERVER_4064
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
