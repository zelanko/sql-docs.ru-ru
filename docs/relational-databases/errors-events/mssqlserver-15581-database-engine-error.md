---
description: MSSQLSERVER_15581
title: MSSQLSERVER_15581
ms.custom: ''
ms.date: 09/03/2020
ms.prod: sql
ms.reviewer: ramakoni1, pijocoder, suresh-kandoth, Masha, VenCher
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15581 (Database Engine error)
ms.assetid: ''
author: suresh-kandoth
ms.author: ramakoni
ms.openlocfilehash: f1221474d86d95400ca955d64b4a0812cffe1c0d
ms.sourcegitcommit: f87f2f0f1edc91fe400040d8e3a5810347aa8d70
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96868918"
---
# <a name="mssqlserver_15581"></a>MSSQLSERVER_15581
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

## <a name="details"></a>Сведения

|attribute|Значение|
|---|---|
|Название продукта|SQL Server|
|Идентификатор события|15581|
|Источник события|MSSQLSERVER|
|Компонент|SQLEngine|
|Символическое имя|SEC_NODBMASTERKEYERR|
|Текст сообщения|Создайте главный ключ в базе данных или откройте его в сеансе до выполнения этой операции.|
||

## <a name="explanation"></a>Объяснение

Ошибка 15581 происходит, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается восстановить базу данных, для которой включено прозрачное шифрование данных (TDE). В журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывается сообщение об ошибке наподобие следующего:

> 2020-01-14 22:16:26.47 spid20s Ошибка: 15581, серьезность: 16, состояние: 3.  
2020-01-14 22:16:26.47 spid20s Создайте главный ключ в базе данных или откройте его в сеансе до выполнения этой операции.

## <a name="possible-cause"></a>Возможные причины

Эта проблема возникает, когда при выполнении следующей команды отменяется шифрование главного ключа базы данных в базе данных master с помощью главного ключа службы:

```sql
Use master
go
alter master key drop encryption by service master key
```

Главный ключ службы применяется для шифрования сертификата, используемого главным ключом базы данных. Для использования базы данных с включенным шифрованием TDE требуется доступ к главному ключу базы данных в базе данных master. Главный ключ, который не зашифрован с помощью главного ключа службы, следует открывать с помощью инструкции [OPEN MASTER KEY (Transact-SQL)](/sql/t-sql/statements/open-master-key-transact-sql) и пароля в каждом сеансе, требующем доступа к главному ключу. Так как эта команда не может выполняться в системных сеансах, восстановление баз данных с включенным шифрованием TDE невозможно.

## <a name="user-action"></a>Рекомендуемые действия

Чтобы устранить эту проблему, включите автоматическую расшифровку главного ключа. Для этого выполните следующие команды.

```sql
Use master
go
open master key DECRYPTION BY PASSWORD = 'password'
alter master key add encryption by service master key
```

Чтобы определить, отключена ли автоматическая расшифровка главного ключа с помощью главного ключа службы для базы данных master, используйте следующий запрос:

```sql
select is_master_key_encrypted_by_server from sys.databases where name = 'master'
```

Если этот запрос возвращает значение 0, автоматическая расшифровка главного ключа с помощью главного ключа службы отключена.

## <a name="more-information"></a>Дополнительные сведения

В некоторых случаях экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может не отвечать на запросы. При запросе к динамическому административному представлению `sys.dm_exec_requests` видно, что поток `LogWriter` и другие потоки, выполняющие операции DML, ожидают неограниченное время с WRITELOG wait_type. Другие сеансы также могут находиться в ожидании при попытке получения блокировок.
