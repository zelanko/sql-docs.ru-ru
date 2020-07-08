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
ms.openlocfilehash: 711f182407fa3b06c48fd81d36dcf80558adaf90
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717864"
---
# <a name="mssqlserver_4064"></a>MSSQLSERVER_4064
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
