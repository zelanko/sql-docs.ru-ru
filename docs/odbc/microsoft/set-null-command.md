---
title: SET NULL Командование (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c83c9ef9f8a0ce143308b73d8df09b05fb2cdea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300814"
---
# <a name="set-null-command"></a>Команда SET NULL
Определяет, как нулевые значения поддерживаются командами ALTER TABLE - S'L, CREATE TABLE - S'L и INSERT - S-L.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера; по умолчанию для Visual FoxPro является OFF.) Уточняется, что все столбцы в таблице, созданной с помощью ALTER TABLE и CREATE TABLE, позволят нулевым значениям. Вы можете переопределить поддержку нулевого значения для столбцов в таблице, включив положение NOT NULL в определения столбцов.  
  
 Также указывается, что INSERT - S'L введет нулевые значения в любые столбцы, не включенные в положение INSERT - S'L VALUE. INSERT - СЗЛ будет вставлять нулевые значения только в столбцы, которые позволяют нулевые значения.  
  
 OFF  
 Уточняется, что все столбцы в таблице, созданной с помощью ALTER TABLE и CREATE TABLE, не допустят нулевых значений. Поддержку нулевого значения можно обозначать для столбцов ALTER TABLE и CREATE TABLE, включив пункт NULL в определения столбцов.  
  
 Также указывается, что INSERT - S'L вставит пустые значения в любые столбцы, не включенные в положение INSERT - S'L VALUE.  
  
## <a name="remarks"></a>Remarks  
 SET NULL влияет только на то, как нулевые значения поддерживаются ALTER TABLE, CREATE TABLE и INSERT - S'L. Другие команды не затрагиваются SET NULL.  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE - Командование СЗЛ](../../odbc/microsoft/alter-table-sql-command.md)   
 [CREATE TABLE - Командование СЗЛ](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT (команда SQL)](../../odbc/microsoft/insert-sql-command.md)
