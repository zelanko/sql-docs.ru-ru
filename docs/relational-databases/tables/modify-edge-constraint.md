---
title: Изменение ограничений ребер | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- alter edge constraints
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5b6a471156f0b1371c727ce96aac72f4f812dac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650252"
---
# <a name="modify-edge-constraints"></a>Изменение ограничений ребер
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Изменить ограничение ребра можно в [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Вы можете изменить ограничение ребер таблицы ребер, изменив порядок его предложения или добавив новое предложение.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Изменение ограничения ребер с помощью:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL
 Чтобы изменить ограничение ребер с помощью Transact-SQL, необходимо сначала удалить имеющееся ограничение, а затем создать его повторно с помощью нового определения. Дополнительные сведения см. в статьях [Удаление ограничений ребер](../../relational-databases/tables/delete-edge-constraint.md) и [Создание ограничений ребер](../../relational-databases/tables/create-edge-constraints.md).    
 
