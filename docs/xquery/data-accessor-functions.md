---
title: Функции методов доступа к данным | Документация Майкрософт
description: 'Узнайте, как использовать функции методов доступа к данным XQuery fn: data (), fn: String () и Text ().'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c8ce28b47fddca3a9c948cf913759e9a07d4419
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753660"
---
# <a name="data-accessor-functions"></a>Функции метода доступа к данным
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  В темах этого раздела приводятся и обсуждаются образцы кода с использованием функций доступа к данным.  
  
## <a name="understanding-fndata-fnstring-and-text"></a>Основные сведения о функциях fn:data(), fn:string(), и text()  
 В XQuery имеется функция **fn: data ()** для извлечения скалярных, типизированных значений из узлов, тестового **текста узла ()** для возврата текстовых узлов и функции **fn: String ()** , возвращающей строковое значение узла. Их применение понятно далеко не всем. Ниже приведены рекомендации по правильному использованию этих функций в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Экземпляр XML \<age> 12 \</age> используется в целях иллюстрации.  
  
-   Нетипизированный XML: выражение пути/аже/текст () возвращает текстовый узел "12". Функции fn:data(/age) и fn:string(/age) возвращают строковое значение«12».  
  
-   Типизированный XML: выражение/аже/текст () возвращает статическую ошибку для любого простого типизированного \<age> элемента. С другой стороны, функция fn:data(/age) возвращает целое число 12. Функция fn:string(/age) возвращает строку «12».  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Строковая функция &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [Функция данных &#40;XQuery&#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>См. также  
 [Выражения пути &#40;XQuery&#41;](../xquery/path-expressions-xquery.md)  
  
  
