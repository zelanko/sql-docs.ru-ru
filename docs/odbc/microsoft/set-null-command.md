---
description: Команда SET NULL
title: SET NULL Command | Документация Майкрософт
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
ms.openlocfilehash: 5e98037838325a0bfe56b51cdcfec7df8539facd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421848"
---
# <a name="set-null-command"></a>Команда SET NULL
Определяет, как значения NULL поддерживаются командами ALTER TABLE-SQL, CREATE TABLE-SQL и INSERT-SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (Значение по умолчанию для драйвера; значение по умолчанию для Visual FoxPro — OFF.) Указывает, что все столбцы в таблице, созданной с помощью инструкции ALTER TABLE и CREATE TABLE, будут допускать значения NULL. Можно переопределить поддержку значений NULL для столбцов в таблице, включив предложение NOT NULL в определениях столбцов.  
  
 Также указывает, что инструкция INSERT-SQL вставит значения NULL в любые столбцы, не входящие в предложение INSERT-SQL VALUE. Инструкция INSERT-SQL вставит значения NULL только в столбцы, допускающие значения NULL.  
  
 OFF  
 Указывает, что все столбцы в таблице, созданной с помощью инструкции ALTER TABLE и CREATE TABLE, не будут допускать значения NULL. Можно назначить поддержку значений NULL для столбцов в инструкции ALTER TABLE и CREATE TABLE, включив предложение NULL в определениях столбцов.  
  
 Также указывает, что инструкция INSERT-SQL вставит пустые значения в любые столбцы, не входящие в предложение INSERT-SQL VALUE.  
  
## <a name="remarks"></a>Remarks  
 SET NULL влияет только на то, как в инструкциях ALTER TABLE, CREATE TABLE и INSERT-SQL поддерживаются значения NULL. На другие команды не влияет установка значения NULL.  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE-команда SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [Команда CREATE TABLE-SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT (команда SQL)](../../odbc/microsoft/insert-sql-command.md)
