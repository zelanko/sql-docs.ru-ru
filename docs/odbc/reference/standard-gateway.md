---
title: Стандартный шлюз | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6bcff520d89d9f188292f8d30632a9e05e358efa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915689"
---
# <a name="standard-gateway"></a>Стандартный шлюз
Объект *шлюза* — это программное обеспечение, которое вызывает один СУБД должен выглядеть как другой. Т. е шлюз принимает интерфейс программирования, грамматику SQL и данных протокола один СУБД и переводит его в программный интерфейс грамматику SQL, и протокол скрытые СУБД потока данных. Например приложения, написанные для использования Microsoft® SQL Server™ можно также доступ к данным DB2 через шлюз DB2 Micro Decisionware; Этот продукт в результате DB2, как SQL Server. При использовании шлюзов, другой шлюз должен быть написан для каждой целевой базы данных.  
  
 Несмотря на то, что шлюзы ограничиваются архитектурных различий между СУБД, они являются хорошим кандидатом для стандартизации. Тем не менее если все СУБД стандартизировать интерфейс программирования, грамматику SQL и данные потока протокола один СУБД, которого СУБД — выбирается в качестве стандартной? Наверняка не коммерческих поставщиков СУБД наверняка согласятся стандартизировать продукт конкурента. Если разрабатываются стандартный интерфейс программирования, грамматику SQL и протокол потока данных, шлюз не требуется.
