---
title: Инструкции | Документы Microsoft
ms.custom: ''
ms.date: 04/17/2020
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d8d6f62a-e815-425c-a80e-a63fd34ec275
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 287b86bd9cc368d2a04ea7f7be5e1397e2d6aab9
ms.sourcegitcommit: 2e6c4104dca8680064eb64a7a79a3e15e1b4365f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2020
ms.locfileid: "85942909"
---
# <a name="transact-sql-statements"></a>Инструкции Transact-SQL

[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Инструкция SQL — это атомарная единица работы, которая либо целиком завершается успешно, либо целиком завершается сбоем. Инструкция SQL — это набор инструкций, состоящий из идентификаторов, параметров, переменных, имен, типов данных и зарезервированных слов SQL, которые успешно компилируются. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создает *неявную* транзакцию для инструкции SQL, если команда `BeginTransaction` не задает начало транзакции. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] всегда фиксирует неявную транзакцию, если инструкция будет выполнена успешно, и откатывают неявную транзакцию при сбое команды.  

Существует много типов инструкций. Пожалуй, самая важная из них — это [SELECT](../queries/select-transact-sql.md), которая возвращает строки из базы данных и позволяет делать выборку одной или нескольких строк или столбцов из одной или нескольких таблиц в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этой статье перечислены категории инструкций для использования с Transact-SQL (T-SQL) в дополнение к инструкции `SELECT`. Полный список инструкций приводится слева.

## <a name="backup-and-restore"></a>Резервное копирование и восстановление

Инструкции резервного копирования и восстановления позволяют создавать резервные копии и восстанавливать данные из резервных копий.  Дополнительные сведения см. в разделе [Общие сведения о резервном копировании и восстановлении](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).

## <a name="data-definition-language"></a>Язык описания данных DDL

Инструкции языка описания данных DDL определяют структуры данных. Эти инструкции используются для создания, изменения и удаления структур данных в базе данных. Эти инструкции включают в себя:

- ALTER
- Параметры сортировки
- CREATE
- DROP
- DISABLE TRIGGER
- ENABLE TRIGGER
- RENAME
- UPDATE STATISTICS

## <a name="data-manipulation-language"></a>Язык обработки данных DML

Язык обработки данных (DML) влияет на информацию, хранящуюся в базе данных. Эти инструкции используются для вставки, обновления и изменение строк в базе данных.

- BULK INSERT
- DELETE
- INSERT
- SELECT
- UPDATE
- MERGE
- TRUNCATE TABLE

## <a name="permissions-statements"></a>Инструкции разрешений

Инструкции разрешений определяют пользователей и имена входа, которые имеют доступ к данным и могут выполнять операции. Дополнительные сведения о проверке подлинности и доступе см. в разделе [Центра безопасности](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="service-broker-statements"></a>Инструкции компонента Service Broker

Service Broker — это компонент, который обеспечивает собственную поддержку приложений обмена сообщениями и приложений с очередями. Дополнительные сведения см. в разделе [Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md).

## <a name="session-settings"></a>Параметры сеанса

Инструкции SET определяют, как текущий сеанс управляет параметрами времени выполнения. Общие сведения см. в разделе [Инструкций SET](set-statements-transact-sql.md).
