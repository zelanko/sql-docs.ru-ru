---
title: Поставщики данных | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ddd360c49c3cbd10b76dc39e6c161a523a93b1bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="data-providers"></a>Поставщики данных
Поставщики данных представляют различных источников данных, таких как базы данных SQL, индексно последовательных файлах, электронные таблицы, сохраняет документ и файлы сообщений. Поставщики предоставляют данные равномерно с помощью общих абстракции вызывается набора строк.  
  
 ADO — мощная и гибкая, так как он может подключиться к одному из нескольких разных поставщиков данных и по-прежнему предоставляют такую же модель программирования, независимо от конкретных функциях любой заданный поставщик. Тем не менее поскольку каждого поставщика данных, взаимодействие приложения с помощью ADO зависит от поставщика данных.  
  
 Например возможности и функции поставщика OLE DB для SQL Server, который используется для доступа к базам данных Microsoft SQL Server, существенно отличаются от тех поставщик Microsoft OLE DB для публикаций в Интернете, который используется для доступа к файлу магазинов на веб-сервере.
