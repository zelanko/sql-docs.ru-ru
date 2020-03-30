---
title: MSSQLSERVER_617 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5078c98445587dbf8c8b99fa18fed4df2ca5846
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67951667"
---
# <a name="mssqlserver_617"></a>MSSQLSERVER_617
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|617|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NODESHASH|  
|Текст сообщения|Дескриптор объекта с идентификатором %ld в базе данных с идентификатором %d не обнаружен в хэш-таблице при попытке его восстановления по хэшу. В рабочей таблице отсутствует запись. Повторите запрос. Если используется курсор, закройте и заново откройте его.|  
  
## <a name="explanation"></a>Объяснение  
SQL Server не может найти рабочую таблицу для конкретной записи.  
  
## <a name="user-action"></a>Действие пользователя  
  
1.  Если используется курсор, закройте и заново откройте его.  
  
2.  Повторите запрос.  
  
