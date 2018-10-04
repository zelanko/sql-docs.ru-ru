---
title: Коды ошибок DataControl | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], DataControl
- DataControl errors [ADO]
ms.assetid: 293df9d5-e1a2-406d-9107-07bf7cdc6f96
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa058add661ba5dc4054a431e0324f97e1efb422
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753106"
---
# <a name="datacontrol-object-error-codes"></a>Коды ошибок DataControl объекта
В следующей таблице перечислены [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта коды ошибок. Положительное десятичное преобразование низкой два байта, показаны отрицательное десятичное преобразование кода ошибку переполнения и шестнадцатеричные значения.

|RDS. Коды ошибок DataControl|Количество|Описание|
|---------------------------------|------------|-----------------|
|**IDS_AsyncPending**|4107 -2146824175 0x800A1011|Невозможно выполнить операцию, пока асинхронная операция находится в состоянии ожидания.|
|**IDS_BadInlineTablegram**|4105 -2146824183 0x800A1009|Неправильный встроенный tablegram.|
|**IDS_CantConnect**|4099 -2146824189 0x800A1003|Не удается подключиться к серверу.|
|**IDS_CantCreateObject**|4100 -2146824188 0x800A1004|Невозможно создать бизнес-объект.|
|**IDS_CantFindDataspace**|4102 -2146824186 0x800A1006|Свойство пространство данных недопустимо.|
|**IDS_CantInvokeMethod**|4101 -2146824187 0x800A1005|Метод нельзя вызывать в бизнес-объекте.|
|**IDS_CrossDomainWarning**|4112 -2146824170 0x800A1016|Эта страница получает доступ к данным в другом домене. Вы действительно хотите разрешить это? Чтобы избежать появления этого сообщения в Internet Explorer, можно добавить безопасный веб-сайт в зону надежных узлов на **безопасности** вкладке **обозревателя** диалоговое окно.|
|**IDS_InvalidADCClientVersion**|4106 -2146824176 0x800A1010|Недопустимая версия клиента RDS — Клиент более новой версии сервера.|
|**IDS_INVALIDARG**|5376 -2147019520 0x80071500|Один или несколько аргументов являются недопустимыми.|
|**IDS_InvalidBindings**|4097 -2146824191 0x800A1001|Ошибка в свойство привязки.|
|**IDS_InvalidParam**|4110 -2146824172 0x800A1014|Один или несколько аргументов являются недопустимыми.|
|**IDS_NOINTERFACE**|5377 -2147019519 0x80071501|Интерфейс не поддерживается.|
|**IDS_NotReentrant**|4111 -2146824171 0x800A1015|Не удается выполнить запрос обработчика событий во время обработки.|
|**IDS_ObjectNotSafe**|4103 -2146824185 0x800A1007|Параметры безопасности этого компьютера запрещают создание бизнес-объекта.|
|**IDS_RecordsetNotOpen**|4109 -2146824173 0x800A1013|**Набор записей** не открыт.|
|**IDS_ResetInvalidField**|4108 -2146824174 0x800A1012|Столбец, указанный в **SortColumn** или **FilterColumn** не существует.|
|**IDS_RowsetNotUpdateable**|4104 -2146824184 0x800A1008|Набор строк не поддерживает обновление.|
|**IDS_UnexpectedError**|4351 -2146823937 0x800A10FF|Произошла непредвиденная ошибка.|
|**IDS_UpdatesFailed**|4098 -2146824190 0x800A1002|Не удалось обновить базу данных.|
|**IDS_URLMONNotFound**|4119 -2146824169 0x800A1017|DataControl **URL-адрес** свойства требуется системный файл Urlmon.dll, который не удается найти.|

## <a name="see-also"></a>См. также
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)
