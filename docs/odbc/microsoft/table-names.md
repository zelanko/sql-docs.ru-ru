---
title: Имена таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5dd8de055521f4a1831d20a9a34bedb9309d1de6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939785"
---
# <a name="table-names"></a>Имена таблиц
Когда расширения имени dBASE, Microsoft Excel, Paradox, или текст, используемый драйвером, имена таблиц, которые происходят в предложении FROM SELECT или DELETE, после предложение INTO в инструкции INSERT и UPDATE, CREATE TABLE и DROP TABLE может содержать допустимый путь, имя первичного и файл .  
  
 Использование имени таблицы в любом месте инструкции SQL не поддерживает использование пути или расширения, но будет принимать только основное имя (например, EMP из C:\ABC\EMP).  
  
 Корреляционные имена (псевдонимы) может использоваться. Пример:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
