---
title: "ErrorValueEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ErrorValueEnum
helpviewer_keywords:
- ErrorValueEnum enumeration [ADO]
ms.assetid: 9469ba3a-5e4f-4a10-bbb8-a51a6c9660ea
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a79af3564a177da2953b053ce943a2d740e4cc7d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="errorvalueenum"></a>ErrorValueEnum
Указывает тип ADO ошибок во время выполнения.  
  
 Перечислены три вида номер ошибки.  
  
-   Положительное десятичное число — низкий два байта полного числа в десятичном формате. Этот номер отображается в Visual Basic по умолчанию появления сообщения об ошибке. Например, ошибка времени выполнения "3707".  
  
-   Отрицательное десятичных — десятичное перевод номер ошибки переполнения.  
  
-   Шестнадцатеричное — шестнадцатеричное представление номера ошибки переполнения. В четвертой позиции — это код устройства Windows. — Это код устройства, для номера ошибок ADO *A*. Например: 0x800***A***0E7B.  
  
> [!NOTE]
>  Приложения ADO могут передаваться ошибок OLE DB. Как правило, они могут идентифицироваться по код средства Windows для *4*. Например, 0x800***4***.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adErrBoundToCommand**|3707 -2146824581 0x800A0E7B|Не удается изменить **ActiveConnection** свойство **записей** объекта, имеющего **команда** объект в качестве источника.|  
|**adErrCannotComplete**|3732 -2146824556 0x800A0E94|Серверу не удается завершить операцию.|  
|**adErrCantChangeConnection**|3748 -2146824540 0x800A0EA4|Подключение было запрещено. Новое соединение, запрашиваемая имеет разные характеристики от того, уже используется.|  
|**adErrCantChangeProvider**|3220 -2146825068 0X800A0C94|Предоставленный поставщик отличается от той, которая уже используется.|  
|**adErrCantConvertvalue**|3724 -2146824564 0x800A0E8C|Значение данных не может быть преобразовано по причинам, отличным от несоответствия знака или данные переполнения. Например преобразование будет усечение данных.|  
|**adErrCantCreate**|3725 -2146824563 0x800A0E8D|Значение данных не может быть задана или получена за Неизвестный тип данных поля, или поставщика было недостаточно ресурсов для выполнения операции.|  
|**adErrCatalogNotSet**|3747 -2146824541 0x800A0EA3|Для операции требуется допустимый **ParentCatalog**.|  
|**adErrColumnNotOnThisRow**|3726 -2146824562 0x800A0E8E|Это поле не содержит записей.|  
|**adErrDataConversion**|3421 -2146824867 0x800A0D5D|Приложение использует значение имеет неправильный тип для текущей операции.|  
|**adErrDataOverflow**|3721 -2146824567 0x800A0E89|Значение данных слишком велик для представления типа данных поля.|  
|**adErrDelResOutOfScope**|3738 -2146824550 0x800A0E9A|Удалить URL-адрес объекта, выходит за пределы текущей записи.|  
|**adErrDenyNotSupported**|3750 -2146824538 0x800A0EA6|Поставщик не поддерживает ограничения управления доступом.|  
|**adErrDenyTypeNotSupported**|3751 -2146824537 0x800A0EA7|Поставщик не поддерживает запрошенный тип ограниченного использования программ для управления доступом.|  
|**adErrFeatureNotAvailable**|3251 -2146825037 0x800A0CB3|Объект или поставщик не может выполнить запрошенную операцию.|  
|**adErrFieldsUpdateFailed**|3749 -2146824539 0x800A0EA5|Не удалось обновить поля. Для получения дополнительной информации проверьте **состояние** свойство объектов отдельного поля.|  
|**adErrIllegalOperation**|3219 -2146825069 0x800A0C93|Операция не допускается в данном контексте.|  
|**adErrIntegrityViolation**|3719 -2146824569 0x800A0E87|Значение противоречит ограничениям целостности поля данных.|  
|**adErrInTransaction**|3246 -2146825042 0x800A0CAE|**Подключение** объекта не может явно закрыто в транзакции.|  
|**adErrInvalidArgument**|3001 -2146825287 0x800A0BB9|Аргументы имеют неправильный тип, выходят за пределы допустимого диапазона или конфликтуют друг с другом.|  
|**adErrInvalidConnection**|3709 -2146824579 0x800A0E7D|Соединение не может использоваться для выполнения этой операции. Он является closed или недопустимым в этом контексте.|  
|**adErrInvalidParamInfo**|3708 -2146824580 0x800A0E7C|**Параметр** объекта задано неправильно. Несогласованные или неполные данные указаны.|  
|**adErrInvalidTransaction**|3714 -2146824574 0x800A0E82|Координирование транзакции является недопустимым или не запущена.|  
|**adErrInvalidURL**|3729 -2146824559 0x800A0E91|URL-адрес содержит недопустимые символы. Убедитесь, что правильно ввели URL-адрес.|  
|**adErrItemNotFound**|3265 -2146825023 0x800A0CC1|Элемент не найден в коллекции, соответствующий запрошенное имя или порядковый номер.|  
|**adErrNoCurrentRecord**|3021 -2146825267 0x800A0BCD|Либо **BOF** или **EOF** имеет значение True, или текущая запись была удалена. Запрошенная операция требует наличия текущей записи.|  
|**adErrNotExecuting**|3715 -2146824573 0x800A0E83|Операция не может быть выполнена во время выполнения не.|  
|**adErrNotReentrant**|3710 -2146824578 0x800A0E7E|Операция не может выполняться во время обработки события.|  
|**adErrObjectClosed**|3704 -2146824584 0x800A0E78|Операция не разрешена, при закрытии объекта.|  
|**adErrObjectInCollection**|3367 -2146824921 0x800A0D27|Объект уже существует в коллекции. Не удается записать.|  
|**adErrObjectNotSet**|3420 -2146824868 0x800A0D5C|Объект больше не является допустимым.|  
|**adErrObjectOpen**|3705 -2146824583 0x800A0E79|Операция не разрешена, когда открыт объект.|  
|**adErrOpeningFile**|3002 -2146825286 0x800A0BBA|Не удалось открыть файл.|  
|**adErrOperationCancelled**|3712 -2146824576 0x800A0E80|Операция была отменена пользователем.|  
|**adErrOutOfSpace**|3734 -2146824554 0x800A0E96|Невозможно выполнить операцию. Поставщик не может получить недостаточно места на диске.|  
|**adErrPermissionDenied**|3720 -2146824568 0x800A0E88|Недостаточно разрешений предотвращает запись в поле.|  
|**adErrProviderFailed**|3000 -2146825288 0x800A0BB8|Поставщику не удалось выполнить запрошенную операцию.|  
|**adErrProviderNotFound**|3706 -2146824582 0x800A0E7A|Не удается найти поставщика. Он может устанавливаться неправильно.|  
|**adErrReadFile**|3003 -2146825285 0x800A0BBB|Не удалось прочитать файл.|  
|**adErrResourceExists**|3731 -2146824557 0x800A0E93|Невозможно выполнить операцию копирования. Объект с именем URL-адрес назначения уже существует. Укажите **adCopyOverwrite** объект.|  
|**adErrResourceLocked**|3730 -2146824558 0x800A0E92|Объект, представленный указанным URL-адрес заблокирован один или несколько процессов. Дождитесь завершения процесса и повторите попытку.|  
|**adErrResourceOutOfScope**|3735 -2146824553 0x800A0E97|URL-адрес источника или назначения, выходит за пределы текущей записи.|  
|**adErrSchemaViolation**|3722 -2146824566 0x800A0E8A|Значение совпадает с типом данных или ограничения поля данных.|  
|**adErrSignMismatch**|3723 -2146824565 0x800A0E8B|Преобразование завершилось неудачей, так как значение данных было со знаком, а тип данных поля, используемый поставщиком без знака.|  
|**adErrStillConnecting**|3713 -2146824575 0x800A0E81|Операция не может выполняться при подключении асинхронно.|  
|**adErrStillExecuting**|3711 -2146824577 0x800A0E7F|Операция не может выполняться во время выполнения в асинхронном режиме.|  
|**adErrTreePermissionDenied**|3728 -2146824560 0x800A0E90|Недостаточно разрешений для доступа к дерева или поддерева.|  
|**adErrUnavailable**|3736 -2146824552 0x800A0E98|Операция не завершена, и состояние недоступна. Возможно, поле или операция не выполнялась.|  
|**adErrUnsafeOperation**|3716 -2146824572 0x800A0E84|Параметры безопасности на этом компьютере предотвратить доступ к источнику данных в другом домене.|  
|**adErrURLDoesNotExist**|3727 -2146824561 0x800A0E8F|URL-адрес источника или родительский URL-адрес назначения не существует.|  
|**adErrURLNamedRowDoesNotExist**|3737 -2146824551 0x800A0E99|Запись с таким именем не существует.|  
|**adErrVolumeNotFound**|3733 -2146824555 0x800A0E95|Поставщик не удается найти URL-адрес устройства хранения. Убедитесь, что правильно ввели URL-адрес.|  
|**adErrWriteFile**|3004 -2146825284 0x800A0BBC|Запись в файл не удалось.|  
|**adWrnSecurityDialog**|3717 -2146824571 0x800A0E85|Только для внутреннего применения. Не используйте.|  
|**adWrnSecurityDialogHeader**|3718 -2146824570 0x800A0E86|Только для внутреннего применения. Не используйте.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
 Определены следующие подмножества ADO/WFC эквиваленты.  
  
|Константа|  
|--------------|  
|AdoEnums.ErrorValue.BOUNDTOCOMMAND|  
|AdoEnums.ErrorValue.DATACONVERSION|  
|AdoEnums.ErrorValue.FEATURENOTAVAILABLE|  
|AdoEnums.ErrorValue.ILLEGALOPERATION|  
|AdoEnums.ErrorValue.INTRANSACTION|  
|AdoEnums.ErrorValue.INVALIDARGUMENT|  
|AdoEnums.ErrorValue.INVALIDCONNECTION|  
|AdoEnums.ErrorValue.INVALIDPARAMINFO|  
|AdoEnums.ErrorValue.ITEMNOTFOUND|  
|AdoEnums.ErrorValue.NOCURRENTRECORD|  
|AdoEnums.ErrorValue.NOTEXECUTING|  
|AdoEnums.ErrorValue.NOTREENTRANT|  
|AdoEnums.ErrorValue.OBJECTCLOSED|  
|AdoEnums.ErrorValue.OBJECTINCOLLECTION|  
|AdoEnums.ErrorValue.OBJECTNOTSET|  
|AdoEnums.ErrorValue.OBJECTOPEN|  
|AdoEnums.ErrorValue.OPERATIONCANCELLED|  
|AdoEnums.ErrorValue.PROVIDERNOTFOUND|  
|AdoEnums.ErrorValue.STILLCONNECTING|  
|AdoEnums.ErrorValue.STILLEXECUTING|  
|AdoEnums.ErrorValue.UNSAFEOPERATION|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Коды ошибок объектов ADO](../../../ado/guide/appendixes/ado-error-codes.md)
