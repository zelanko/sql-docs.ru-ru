---
title: Анализ данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parsing [Integration Services]
- data parsing [Integration Services]
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7517819f2cf6909cd95d76043519f78b06699b6c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192482"
---
# <a name="parsing-data"></a>Анализ данных
  Потоки данных в пакетах извлекают и загружают данные между разнородными хранилищами данных, которые могут использовать различные стандартные и пользовательские типы данных. В потоке данных источники служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] выполняют извлечение, анализ строковых данных и преобразование в тип данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Последующие преобразования могут анализировать данные для их преобразования в другой тип данных или для создания копий столбцов с различными типами данных. Выражения, используемые в компонентах, могут также приводить аргументы и операнды к различным типам данных. Наконец, когда данные загружены в хранилище данных, целевой объект может проанализировать данные для их преобразования в используемый этим назначением тип данных. Дополнительные сведения см. в статье [Integration Services Data Types](integration-services-data-types.md).  
  
## <a name="types-of-parsing"></a>Типы синтаксического анализа  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предусматривают два типа анализа для преобразования данных: быстрый и стандартный синтаксический анализ.  
  
-   Быстрый анализ — это быстрый, простой набор операций анализа, не поддерживающий преобразования местных типов данных и поддерживающий только наиболее часто используемые форматы даты и времени. Дополнительные сведения см. в статье [Fast Parse](../fast-parse.md).  
  
-   Стандартный анализ — это большой набор операций анализа, поддерживающий преобразования всех типов данных, предусмотренных интерфейсами автоматического преобразования типов данных API-интерфейса в библиотеках Oleaut32.dll и Ole2dsip.dll. Дополнительные сведения см. в статье [Standard Parse](../standard-parse.md).  
  
  