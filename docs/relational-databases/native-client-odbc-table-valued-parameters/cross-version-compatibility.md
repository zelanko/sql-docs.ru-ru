---
title: Совместимость между версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 196c99bebaf0255f095055bef6c9c6a64c41908b
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73776287"
---
# <a name="cross-version-compatibility"></a>Совместимость версий
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Конфликты между версиями могут происходить, если экземпляры клиента или сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], предшествующие [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], участвуют в обработке возвращающих табличное значение параметров.  
  
 В общем случае функциональные возможности возвращающих табличное значение параметров доступны только клиентам [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (с помощью собственного клиента SQL Server версии 10.0) или более поздних версий, соединенных с серверами [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии). Новые столбцы в результирующих наборах функций каталога будут представлены только при подключении к серверу [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии).  
  
 Если клиентское приложение, скомпилированное с помощью собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущей версии, выполняет инструкции, которые ожидают возвращающие табличное значение параметры, то сервер определяет это условие как ошибку преобразования данных, и ODBC возвращает код SQLSTATE 07006 и сообщение «Нарушение атрибута ограниченного типа данных».  
  
 Если клиентское приложение, которое было скомпилировано с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10,0 или более поздней версии, пытается использовать возвращающие табличное значение параметры при подключении к экземпляру сервера более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент обнаружит это, и SQLBindCol, SQLBindParameter, Вызовы Склсетдескфиелдс и SQLSetDescRec завершатся ошибкой с кодом SQLSTATE 07006 и сообщением "нарушение атрибута ограниченного типа данных (версия SQL Server для этого соединения не поддерживает возвращающие табличные значения параметры)".  
  
## <a name="see-also"></a>См. также раздел  
 [Возвращающие табличные значения параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
