---
description: ResyncEnum
title: Ресинценум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 0c98c0b0bae307f57e5a77c7ca4ac6b473f4d149
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989465"
---
# <a name="resyncenum"></a>ResyncEnum
Указывает, перезаписываются ли базовые значения при вызове повторной [синхронизации](./resync-method.md).  
  
|Константа|Значение|Описание|  
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