---
title: Stream объект (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream
helpviewer_keywords:
- Stream object [ADO]
ms.assetid: 0514531f-009d-4519-abc3-d727014a39f1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 976e822482efc530e3b055f61c242ee03a30e012
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63179831"
---
# <a name="stream-object-ado"></a>Объект Stream (ADO)
Представляет поток двоичных данных или текста.  
  
 В древовидной иерархии файловой системы или системы электронной почты [записи](../../../ado/reference/ado-api/record-object-ado.md) возможно, по умолчанию двоичный поток битов, связанные с ней, содержащий содержимое файла или сообщения электронной почты. Объект **Stream** объект может использоваться для обработки поля или записи, содержащие эти потоки данных. Объект **Stream** может быть получен следующими способами:  
  
-   Из URL-адрес, указывающий на объект (как правило, файл), содержащий двоичные или текстовые данные. Этот объект может быть простой документ, **записи** объект, представляющий структурированного документа или папки.  
  
-   Значение по умолчанию, открыв **Stream** объект, связанный с **записи** объекта. Вы можете получить поток по умолчанию, связанные с **записи** объекта при **записи** открыт, чтобы исключить передача просто открыть поток.  
  
-   Путем создания экземпляра **Stream** объекта. Эти **Stream** объекты могут использоваться для хранения данных в рамках приложения. В отличие от **Stream** связанный с URL-адрес, или значение по умолчанию **Stream** из **записи**, которого создан экземпляр **Stream** не связан ни с базового источника по умолчанию.  
  
 С помощью методов и свойств **Stream** объекта, можно сделать следующее:  
  
-   Откройте **Stream** объекта из **записи** или URL-адрес с [откройте](../../../ado/reference/ado-api/open-method-ado-stream.md) метод.  
  
-   Закрыть **Stream** с [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод.  
  
-   Входные данные байт или текст, **Stream** с [записи](../../../ado/reference/ado-api/write-method.md) и [WriteText](../../../ado/reference/ado-api/writetext-method.md) методы.  
  
-   Считывает байты из **Stream** с [чтения](../../../ado/reference/ado-api/read-method.md) и [ReadText](../../../ado/reference/ado-api/readtext-method.md) методы.  
  
-   Напишите **Stream** буфера данных по-прежнему в ADO к базовому объекту с [Flush](../../../ado/reference/ado-api/flush-method-ado.md) метод.  
  
-   Скопируйте содержимое **Stream** в другой **Stream** с [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) метод.  
  
-   Контролировать, каким образом строки считываются из исходного файла с [SkipLine](../../../ado/reference/ado-api/skipline-method.md)метод и [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) свойство.  
  
-   Определить конец позицию в потоке [EOS](../../../ado/reference/ado-api/eos-property.md)свойство и [SetEOS](../../../ado/reference/ado-api/seteos-method.md) метод.  
  
-   Сохранять и восстанавливать данные в файлах с [SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)и [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md) методы.  
  
-   Укажите набор символов, используемый для хранения **Stream** с [Charset](../../../ado/reference/ado-api/charset-property-ado.md) свойство.  
  
-   Halt асинхронную **Stream** операцию с [отменить](../../../ado/reference/ado-api/cancel-method-ado.md) метод.  
  
-   Определить количество байтов в **Stream** с [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) свойство.  
  
-   Управлять текущую позицию внутри **Stream** с [позиции](../../../ado/reference/ado-api/position-property-ado.md) свойство.  
  
-   Определить тип данных в **Stream** с [тип](../../../ado/reference/ado-api/type-property-ado-stream.md) свойства.  
  
-   Определить текущее состояние **Stream** (закрыто, откройте или выполнение) с [состояние](../../../ado/reference/ado-api/state-property-ado.md) свойство.  
  
-   Укажите режим доступа для **Stream** с [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 **Stream** объект безопасен для скриптов.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства объекта Stream, методы и события](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Записи и потоки](../../../ado/guide/data/records-and-streams.md)
