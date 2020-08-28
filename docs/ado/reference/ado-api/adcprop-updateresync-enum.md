---
description: ADCPROP_UPDATERESYNC_ENUM
title: ADCPROP_UPDATERESYNC_ENUM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
author: rothja
ms.author: jroth
ms.openlocfilehash: 2fcf60974612325e8af7501eaa6066d96d9f2985
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976825"
---
# <a name="adcprop_updateresync_enum"></a>ADCPROP_UPDATERESYNC_ENUM
Указывает, следует ли за методом [UpdateBatch](./updatebatch-method.md) выполнить неявную операцию повторной [синхронизации](./resync-method.md) и, если да, область действия этой операции.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Вызывает **повторную синхронизацию** с объединенным значением всех остальных членов ADCPROP_UPDATERESYNC_ENUM.|  
|**адресинкаутоинкремент**|1|По умолчанию. Пытается получить новое значение идентификатора для столбцов, которые автоматически увеличиваются или генерируются источником данных, например поля автонумерации Microsoft Jet или Microsoft SQL Server столбцы идентификаторов.|  
|**adResyncConflicts**|2|Вызывает **повторную синхронизацию** для всех строк, в которых произошел сбой операции обновления или удаления из-за конфликта параллелизма.|  
|**адресинЦинсертс**|8|Вызывает **повторную синхронизацию** для всех успешно вставленных строк. Однако значения столбца AutoIncrement не синхронизируются повторно. Вместо этого содержимое вновь вставленных строк синхронизируется повторно на основе существующего значения первичного ключа. Если первичный ключ является значением автоприращения, то **Повторная синхронизация** не будет извлекать содержимое предполагаемой строки. Для автоматического увеличения значений первичного ключа автоприращения вызовите **UpdateBatch** с объединенным значением **адресинкаутоинкремент**  +  **адресинЦинсертс**.|  
|**адресинкноне**|0|Не вызывает **повторную синхронизацию**.|  
|**адресинкупдатес**|4|Вызывает **повторную синхронизацию** для всех успешно обновленных строк.|  
  
## <a name="applies-to"></a>Применение  
 [Свойство Update Resync (динамическое) (ADO)](./update-resync-property-dynamic-ado.md)