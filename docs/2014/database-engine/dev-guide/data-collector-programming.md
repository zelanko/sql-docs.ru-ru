---
title: Программирование сборщика данных | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data collector [SQL Server], programming
ms.assetid: 53b4752b-055d-4716-b2bc-75b4cce84101
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a9a3e4428eee6057ac3e38e553eec43616504a06
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193631"
---
# <a name="data-collector-programming"></a>Программирование сборщика данных
  API-интерфейс сборщика данных (пространство имен <xref:Microsoft.SqlServer.Management.Collector>) обеспечивает программное управление всеми операциями настройки через объектную модель. Кроме того, многие операции сбора данных, использующие API, реализованы в виде хранимых процедур, установленных на сервере.  
  
 На следующей иллюстрации показаны ключевые элементы модели объектов сборщика данных.  
  
 ![Модель объектов сборщика данных](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "модель объектов сборщика данных")  
  
  