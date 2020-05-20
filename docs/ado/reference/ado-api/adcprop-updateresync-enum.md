---
title: ADCPROP_UPDATERESYNC_ENUM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: d27169aa9da35f84a1d91985f7f2d1a41035a100
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760710"
---
# <a name="adcprop_updateresync_enum"></a>ADCPROP_UPDATERESYNC_ENUM
Указывает, следует ли за методом [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) выполнить неявную операцию повторной [синхронизации](../../../ado/reference/ado-api/resync-method.md) и, если да, область действия этой операции.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Вызывает **повторную синхронизацию** с объединенным значением всех остальных членов ADCPROP_UPDATERESYNC_ENUM.|  
|**адресинкаутоинкремент**|1|По умолчанию. Пытается получить новое значение идентификатора для столбцов, которые автоматически увеличиваются или генерируются источником данных, например поля автонумерации Microsoft Jet или Microsoft SQL Server столбцы идентификаторов.|  
|**adResyncConflicts**|2|Вызывает **повторную синхронизацию** для всех строк, в которых произошел сбой операции обновления или удаления из-за конфликта параллелизма.|  
|**адресинЦинсертс**|8|Вызывает **повторную синхронизацию** для всех успешно вставленных строк. Однако значения столбца AutoIncrement не синхронизируются повторно. Вместо этого содержимое вновь вставленных строк синхронизируется повторно на основе существующего значения первичного ключа. Если первичный ключ является значением автоприращения, то **Повторная синхронизация** не будет извлекать содержимое предполагаемой строки. Для автоматического увеличения значений первичного ключа автоприращения вызовите **UpdateBatch** с объединенным значением **адресинкаутоинкремент**  +  **адресинЦинсертс**.|  
|**адресинкноне**|0|Не вызывает **повторную синхронизацию**.|  
|**адресинкупдатес**|4|Вызывает **повторную синхронизацию** для всех успешно обновленных строк.|  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство Update Resync (динамическое) (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
