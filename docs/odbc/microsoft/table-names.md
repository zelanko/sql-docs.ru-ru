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
manager: craigg
ms.openlocfilehash: 2d72d7868d0e19719ea7992bdb8ccd1f61f3718d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755738"
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
