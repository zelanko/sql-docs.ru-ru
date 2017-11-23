---
title: "Совместимость версий | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4dda2d778124f86681f06921e404472d266b5e41
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="cross-version-compatibility"></a>Совместимость версий
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Конфликты между версиями могут происходить, если экземпляры клиента или сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], предшествующие [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], участвуют в обработке возвращающих табличное значение параметров.  
  
 В общем случае функциональные возможности возвращающих табличное значение параметров доступны только клиентам [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (с помощью собственного клиента SQL Server версии 10.0) или более поздних версий, соединенных с серверами [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии). Новые столбцы в результирующих наборов функции каталога появятся только при подключении к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии) сервера.  
  
 Если клиентское приложение, скомпилированное с помощью собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущей версии, выполняет инструкции, которые ожидают возвращающие табличное значение параметры, то сервер определяет это условие как ошибку преобразования данных, и ODBC возвращает код SQLSTATE 07006 и сообщение «Нарушение атрибута ограниченного типа данных».  
  
 Если клиентское приложение, скомпилированное с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент версии 10.0 или более поздней версии пытается использовать возвращающие табличные значения параметров при подключении к экземпляру сервера более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент обнаружит это и SQLBindCol, SQLBindParameter, SQLSetDescFields и SQLSetDescRec вызовы завершатся ошибкой с кодом SQLSTATE 07006 и сообщением «Ограниченные (версия SQL Server для этого соединения не поддерживает возвращающие табличные значения параметров) нарушение атрибута типа данных».  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличные значения параметры &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
