---
title: ЗАДАТЬ УНИКАЛЬную команду | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063613"
---
# <a name="set-unique-command"></a>Команда SET UNIQUE
Указывает, сохраняются ли записи с повторяющимися значениями ключа индекса в файле индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Указывает, что любая запись с повторяющимися значениями ключа индекса не должна включаться в файл индекса. В файл индекса включаются только первая запись с исходным значением ключа индекса.  
  
 OFF  
 (По умолчанию.) Указывает, что в файл индекса будут включаться записи с повторяющимися значениями ключа индекса.  
  
## <a name="remarks"></a>Remarks  
 При повторном ИНДЕКСИРОВАНии файл индекса остается установленным уникальным параметром SET UNIQUE. Дополнительные сведения см. в разделе [index](../../odbc/microsoft/index-command.md).
