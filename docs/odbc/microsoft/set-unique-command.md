---
description: Команда SET UNIQUE
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8fa4ca11ed5beae08bfcbeb8b5a55d6c2969785
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412460"
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
