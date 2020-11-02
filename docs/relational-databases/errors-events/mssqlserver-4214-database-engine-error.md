---
description: MSSQLSERVER_
title: MSSQLSERVER_4214
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.reviewer: ramakoni1, pijocoder, suresh-kandoth, Masha
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 4214 (Database Engine error)
ms.assetid: ''
author: suresh-kandoth
ms.author: ramakoni
ms.openlocfilehash: 0a04ec00e94dca9a4d940a3b0182123f0716d472
ms.sourcegitcommit: ead0b8c334d487a07e41256ce5d6acafa2d23c9d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92418844"
---
# <a name="mssqlserver_4214"></a>MSSQLSERVER_4214
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

## <a name="details"></a>Сведения

|attribute|Значение|
|---|---|
|Название продукта|SQL Server|
|Идентификатор события|4214|
|Источник события|MSSQLSERVER|
|Компонент|SQLEngine|
|Символическое имя|DMPX_NODBBACKUP|
|Текст сообщения|Инструкцию BACKUP LOG невозможно выполнить, так как не существует резервной копии текущей базы данных.|
||

## <a name="explanation"></a>Пояснение

Эта ошибка возникает при попытке выполнить резервное копирование журнала транзакций перед полным резервным копированием базы данных. Перед тем как выполнять резервное копирование журнала транзакций для базы данных, необходимо произвести ее полное резервное копирование. Кроме того, в журнале ошибок появится следующее сообщение:

> Резервное копирование \<Datetime>    Ошибка: 3041, серьезность: 16, состояние: 1.  
Резервное копирование \<Datetime>     BACKUP не выполнила команду BACKUP LOG \<db_name>. Проверьте дополнительные сообщения в журнале приложения резервного копирования.

## <a name="user-action"></a>Рекомендуемые действия

Перед тем как выполнять резервное копирование журнала транзакций для базы данных, произведите ее полное резервное копирование.

## <a name="more-information"></a>Дополнительные сведения

Дополнительные сведения см. в следующей статье: [Резервное копирование и восстановление баз данных SQL Server](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases).