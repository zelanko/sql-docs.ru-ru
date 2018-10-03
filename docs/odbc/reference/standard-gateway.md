---
title: Стандартный шлюз | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c70a558b065765dd9f8c0895345959e8aa22ebfe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854030"
---
# <a name="standard-gateway"></a>Стандартный шлюз
Объект *шлюза* — это программное обеспечение, которое вызывает один СУБД, чтобы он выглядел другой. Т. е шлюз принимает интерфейс программирования, грамматику SQL и данных протокола единый СУБД и переводит его в интерфейс программирования, грамматику SQL, и протокол скрытые СУБД потока данных. Например приложения, написанные для использования Microsoft® SQL Server™ можно также доступ к данным DB2 через шлюз DB2 Decisionware Micro; Этот продукт приводит к DB2, чтобы он выглядел SQL Server. При использовании шлюзов другой шлюз должен быть написан таким образом, для каждой целевой базы данных.  
  
 Несмотря на то, что шлюзы будут ограничена из-за архитектурных различий между СУБД, они являются хорошим кандидатом для стандартизации. Тем не менее все СУБД, стандартизировать интерфейс программирования грамматики SQL и данных потоковой передачи протокол единого сервера СУБД которого СУБД — выбирается в качестве стандартного? Определенно не коммерческих поставщика СУБД наверняка согласятся стандартизировать продукта конкурента. И если разрабатываются стандартный интерфейс программирования, грамматику SQL и протокол потока данных, шлюз не требуется.
