---
title: Изменения в работе функций длины строки и подстроки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c29b1bd036debc4285f8b0fa0b3cc68bdeb3449
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66096624"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Изменения в работе функций длины строки и подстроки
  [Функция string-length &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) и [substring, функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) функции могут возвращать разные результаты при использовании баз данных XML, содержащих суррогатные символы.  
  
## <a name="description"></a>Описание  
 Если база данных настроена на совместимость с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], поведение [функция string-length &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) и [substring, функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) функции изменения, при работе с символами Юникода. Каждый дополнительный символ Юникода, определяемый по кодовой точке больше чем U+FFFF, считается в этих функциях одним символом, а не двумя, как было в предыдущих версиях.  
  
 Дополнительные сведения о суррогатных символах см. в разделе [Суррогаты и дополнительные символы](https://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
