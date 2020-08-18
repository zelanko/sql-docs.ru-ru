---
description: MSSQLSERVER_9002
title: MSSQLSERVER_9002 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9e35ac85fa3037aa78b75a7f57046f9f9ef53e4d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88331130"
---
# <a name="mssqlserver_9002"></a>MSSQLSERVER_9002
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|9002|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LOG_IS_FULL|  
|Текст сообщения|Журнал транзакций для базы данных «%.*ls» заполнен. Чтобы выяснить, почему пространство журнала не может быть использовано повторно, см. столбец log_reuse_wait_desc в представлении каталога sys.databases.|  
  
## <a name="explanation"></a>Объяснение  
Недостаточно места в журнале базы данных. Столбец **log_reuse_wait_desc** в представлении каталога **sys.databases** показывает, почему пространство журнала не может использоваться повторно.  
  
## <a name="user-action"></a>Действие пользователя  
Используя представление каталога **sys.databases**, определите, почему журнал полон, и исправьте неполадку. Дополнительные сведения см. в разделе «Устранение неполадок в полном журнале транзакций (ошибка 9002)» электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также:  
[Устранение неполадок при переполнении журнала транзакций (ошибка SQL Server 9002)](~/relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
[sys.databases (Transact-SQL)](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
