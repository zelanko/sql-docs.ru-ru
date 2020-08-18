---
description: MSSQLSERVER_10737
title: MSSQLSERVER_10737 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 944f883e73cacf930d5cfff7eb5b59c5e8ed92b6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88337610"
---
# <a name="mssqlserver_10737"></a>MSSQLSERVER_10737
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|10737|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REBUILD_PARTITION_ALL_NOT_SPECIFIED|  
|Текст сообщения|Если в предложении DATA_COMPRESSION инструкции ALTER TABLE REBUILD или ALTER INDEX REBUILD указана секция, то должно быть задано предложение PARTITION=ALL. Предложение PARTITION=ALL используется для подтверждения того, что должны быть перестроены все секции таблицы или индекса, даже если в предложении DATA_COMPRESSION указано только подмножество.|  
  
## <a name="user-action"></a>Действие пользователя  
Добавьте предложение PARTITION=ALL к инструкции ALTER INDEX или ALTER TABLE. Также вы можете перестроить конкретную секцию, используя команду REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}).  
  
