---
title: Команда SET UNIQUE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 29598ed97cba8be04a0c08727cffc40e663becba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063613"
---
# <a name="set-unique-command"></a>Команда SET UNIQUE
Указывает, поддерживаются ли записи с помощью одинаковых значений ключей индекса в файле индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Указывает, что все записи со значением ключа дублированный индекс не включаться в файл индекса. Только первой записи исходное значение ключа индекса включается в файл индекса.  
  
 OFF  
 (по умолчанию). Указывает, что записи с помощью одинаковых значений ключей индекса включаются в файл индекса.  
  
## <a name="remarks"></a>Примечания  
 Файл индекса сохраняет свои ЗАДАТЬ УНИКАЛЬНЫЕ настройки, при выполнении REINDEX. Дополнительные сведения см. в разделе [индекс](../../odbc/microsoft/index-command.md).
