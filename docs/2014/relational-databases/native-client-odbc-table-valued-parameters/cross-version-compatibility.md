---
title: Совместимость между версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f23b0f43b32d737f03cb7c9b00368558e89e9288
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63199993"
---
# <a name="cross-version-compatibility"></a>Совместимость версий
  Конфликты между версиями могут происходить, если экземпляры клиента или сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], предшествующие [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], участвуют в обработке возвращающих табличное значение параметров.  
  
 В общем случае функциональные возможности возвращающих табличное значение параметров доступны только клиентам [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (с помощью собственного клиента SQL Server версии 10.0) или более поздних версий, соединенных с серверами [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии). Новые столбцы в результирующих наборах функций каталога будут представлены только при подключении к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] серверу (или более поздней версии).  
  
 Если клиентское приложение, скомпилированное с помощью собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущей версии, выполняет инструкции, которые ожидают возвращающие табличное значение параметры, то сервер определяет это условие как ошибку преобразования данных, и ODBC возвращает код SQLSTATE 07006 и сообщение «Нарушение атрибута ограниченного типа данных».  
  
 Если клиентское приложение, скомпилированное с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощью собственного клиента 10,0 или более поздней версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], пытается использовать возвращающие табличное значение параметры при соединении с экземпляром сервера, выпущенным ранее, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент обнаружит это, а вызовы SQLBindCol, SQLBindParameter, склсетдескфиелдс и SQLSetDescRec будут завершаться ошибкой с кодом SQLSTATE 07006, а сообщение "нарушение атрибута ограниченного типа данных (версия SQL Server для этого соединения не поддерживает  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличное значение параметры &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
