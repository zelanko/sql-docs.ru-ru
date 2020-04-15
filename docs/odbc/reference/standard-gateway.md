---
title: Стандартный шлюз Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67551845c0dd8c6a28c0c4bc1c50f54ee8232df1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280077"
---
# <a name="standard-gateway"></a>Стандартный шлюз
*Шлюз* — это часть программного обеспечения, которая заставляет один DBMS выглядеть как другой. То есть шлюз принимает интерфейс программирования, грамматику S'L и протокол потока данных одного DBMS и переводит его в интерфейс программирования, грамматику S'L и протокол потока данных скрытого DBMS. Например, приложения, написанные для использования Microsoft® S'L Server™ также могут получить доступ к данным DB2 через Micro Decisionware DB2 Gateway; этот продукт приводит к тому, что DB2 выглядит как сервер S'L. При использовании шлюзов для каждой целевой базы данных необходимо записать другой шлюз.  
  
 Хотя шлюзы ограничены архитектурными различиями между DBMS, они являются хорошим кандидатом на стандартизацию. Однако, если все DBMS должны стандартизировать интерфейс программирования, грамматику S'L и протокол потока данных одного DBMS, чей DBMS должен быть выбран в качестве стандарта? Конечно, ни один коммерческий поставщик DBMS, скорее всего, не согласится стандартизировать продукт конкурента. И если разработан стандартный интерфейс программирования, грамматика S'L и протокол потока данных, шлюз не требуется.
