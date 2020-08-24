---
description: ResyncEnum
title: Ресинценум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
author: rothja
ms.author: jroth
ms.openlocfilehash: addaaa07b14b88ed7d72714ba8698da1f2ef2ac9
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777643"
---
# <a name="resyncenum"></a>ResyncEnum
Указывает, перезаписываются ли базовые значения при вызове повторной [синхронизации](./resync-method.md).  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**адресинкаллвалуес**|2|По умолчанию. Перезаписывает данные, и ожидающие обновления отменяются.|  
|**адресинкундерлингвалуес**|1|Не перезаписывает данные, а ожидающие обновления не отменяются.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Resync. В ALLVALUES|  
|Адоенумс. Resync. УНДЕРЛИНГВАЛУЕС|  
  
## <a name="applies-to"></a>Применение  
 [Метод Resync](./resync-method.md)