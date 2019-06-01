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
ms.openlocfilehash: 18643dfc11d2b1b1d875a19c478f9ec8cbdd5be6
ms.sourcegitcommit: 5905c29b5531cef407b119ebf5a120316ad7b713
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66428845"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Изменения в работе функций длины строки и подстроки
  [Функция string-length &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) и [substring, функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) функции могут возвращать разные результаты при использовании баз данных XML, содержащих суррогатные символы.  
  
## <a name="description"></a>Описание  
 Если база данных настроена на совместимость с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], поведение [функция string-length &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) и [substring, функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) функции изменения, при работе с символами Юникода. Каждый дополнительный символ Юникода, определяемый по кодовой точке больше чем U+FFFF, считается в этих функциях одним символом, а не двумя, как было в предыдущих версиях.  
  
 Дополнительные сведения о суррогатных символах см. в разделе [Суррогаты и дополнительные символы](https://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
