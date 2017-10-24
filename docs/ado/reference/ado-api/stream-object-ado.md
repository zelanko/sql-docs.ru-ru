---
title: "Поток объекта (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Stream
helpviewer_keywords:
- Stream object [ADO]
ms.assetid: 0514531f-009d-4519-abc3-d727014a39f1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b074a26bdd82bd4356620dbd0b12dc0b7f1c75c7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="stream-object-ado"></a>Объект потока (ADO)
Представляет поток двоичных данных или текста.  
  
 В древовидной структурой иерархии файловой системы или системы электронной почты [записи](../../../ado/reference/ado-api/record-object-ado.md) , возможно, по умолчанию двоичного потока битов, связанные с ним, содержащий содержимое файла или сообщения электронной почты. Объект **поток** объект может использоваться для обработки поля или записи, содержащие эти потоки данных. Объект **поток** объекта можно получить следующими способами:  
  
-   Из URL-адрес, указывающий объект (как правило, файл), содержащий двоичные или текстовые данные. Этот объект может быть простой документ **записи** объект, представляющий структурированный документ или папку.  
  
-   Значение по умолчанию, открыв **поток** объекта, связанного с **записи** объекта. Вы можете получить поток по умолчанию, связанные с **запись** объекта при **записи** открыт, чтобы исключить приема-передачи, чтобы открыть поток.  
  
-   Путем создания экземпляра **поток** объекта. Эти **поток** объекты могут использоваться для хранения данных в рамках приложения. В отличие от **поток** связанные с URL-адрес или значение по умолчанию **поток** из **запись**, созданный экземпляр **поток** не связан с основной источник по умолчанию.  
  
 В случае методов и свойств **поток** объекта, можно сделать следующее:  
  
-   Откройте **поток** объекта из **запись** или URL-адрес с [откройте](../../../ado/reference/ado-api/open-method-ado-stream.md) метод.  
  
-   Закрыть **поток** с [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод.  
  
-   Входные байт или текст, **поток** с [записи](../../../ado/reference/ado-api/write-method.md) и [WriteText](../../../ado/reference/ado-api/writetext-method.md) методы.  
  
-   Считывает байты из **поток** с [чтения](../../../ado/reference/ado-api/read-method.md) и [ReadText](../../../ado/reference/ado-api/readtext-method.md) методы.  
  
-   Писать **поток** буфера данных по-прежнему в ADO к базовому объекту с [Flush](../../../ado/reference/ado-api/flush-method-ado.md) метод.  
  
-   Скопируйте содержимое **поток** в другой **поток** с [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) метод.  
  
-   Контролировать порядок считывания строк из исходного файла с [SkipLine](../../../ado/reference/ado-api/skipline-method.md)метод и [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) свойство.  
  
-   Определить конец позицию в потоке [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md)свойство и [SetEOS](../../../ado/reference/ado-api/seteos-method.md) метод.  
  
-   Сохранение и восстановление данных в файлах с [SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)и [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md) методы.  
  
-   Укажите набор знаков, используемый для хранения **поток** с [Charset](../../../ado/reference/ado-api/charset-property-ado.md) свойство.  
  
-   Остановка асинхронных **поток** операции с [отменить](../../../ado/reference/ado-api/cancel-method-ado.md) метод.  
  
-   Определить размер в байтах **поток** с [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) свойство.  
  
-   Управлять текущую позицию внутри **поток** с [позиции](../../../ado/reference/ado-api/position-property-ado.md) свойство.  
  
-   Определить тип данных в **поток** с [тип](../../../ado/reference/ado-api/type-property-ado-stream.md) свойства.  
  
-   Определить текущее состояние **поток** (закрыт, откройте или выполнении) с [состояние](../../../ado/reference/ado-api/state-property-ado.md) свойство.  
  
-   Укажите режим доступа для **поток** с [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 **Поток** объекта безопасные для использования.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства объекта потока, методы и события](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Записи и потоки](../../../ado/guide/data/records-and-streams.md)

