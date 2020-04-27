---
title: Объект Stream (ADO) | Документация Майкрософт
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
ms.openlocfilehash: c70a22a3048c769aac343d51e621e4d755d3baeb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67916722"
---
# <a name="stream-object-ado"></a>Объект Stream (ADO)
Представляет поток двоичных данных или текста.  
  
 В древовидных иерархиях, таких как файловая система или система электронной почты, [запись](../../../ado/reference/ado-api/record-object-ado.md) может иметь двоичный поток по умолчанию, связанный с, который содержит содержимое файла или сообщения электронной почты. Объект **потока** можно использовать для работы с полями или записями, содержащими эти потоки данных. Объект **потока** можно получить следующими способами:  
  
-   Из URL-адреса, указывающего на объект (обычно файл), содержащий двоичные или текстовые данные. Этот объект может быть простым документом, объектом **записи** , представляющим структурированный документ, или папкой.  
  
-   Открыв объект **потока** по умолчанию, связанный с объектом **Record** . Можно получить поток по умолчанию, связанный с объектом **Record** при открытии **записи** , чтобы исключить цикл обработки, чтобы открыть поток.  
  
-   Путем создания экземпляра объекта **потока** . Эти объекты **потоков** можно использовать для хранения данных в целях приложения. В отличие от **потока** , связанного с URL-адресом, или **потока** **записи**по умолчанию, экземпляр **потока** по умолчанию не связан с базовым источником.  
  
 С помощью методов и свойств объекта **Stream** можно выполнять следующие действия.  
  
-   Откройте объект **потока** из **записи** или URL-адреса с помощью метода [Open](../../../ado/reference/ado-api/open-method-ado-stream.md) .  
  
-   Закройте **поток** с помощью метода [Close](../../../ado/reference/ado-api/close-method-ado.md) .  
  
-   Входные байты или текстовые данные в **поток** с помощью методов [Write](../../../ado/reference/ado-api/write-method.md) и [WriteText](../../../ado/reference/ado-api/writetext-method.md) .  
  
-   Считывает байты из **потока** с помощью методов [Read](../../../ado/reference/ado-api/read-method.md) и [ReadText](../../../ado/reference/ado-api/readtext-method.md) .  
  
-   Запишите все данные **потока** в БУФЕРе ADO в базовый объект с помощью метода [flush](../../../ado/reference/ado-api/flush-method-ado.md) .  
  
-   Скопируйте содержимое **потока** в другой **поток** с помощью метода [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) .  
  
-   Управление способом считывания строк из исходного файла с помощью метода [скиплине](../../../ado/reference/ado-api/skipline-method.md)и свойства [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) .  
  
-   Определите конец потокового расположения с помощью свойства [EOS](../../../ado/reference/ado-api/eos-property.md)и метода [сетеос](../../../ado/reference/ado-api/seteos-method.md) .  
  
-   Сохранение и восстановление данных в файлах с помощью методов [SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)и [лоадфромфиле](../../../ado/reference/ado-api/loadfromfile-method-ado.md) .  
  
-   Укажите кодировку, используемую для хранения **потока** , с помощью свойства [CharSet](../../../ado/reference/ado-api/charset-property-ado.md) .  
  
-   Остановите асинхронную операцию **потока** с помощью метода [Cancel](../../../ado/reference/ado-api/cancel-method-ado.md) .  
  
-   Определите число байтов в **потоке** с помощью свойства [size](../../../ado/reference/ado-api/size-property-ado-stream.md) .  
  
-   Управление текущей позицией в **потоке** с помощью свойства " [позиционирование](../../../ado/reference/ado-api/position-property-ado.md) ".  
  
-   Определите тип данных в **потоке** с помощью свойства [Type](../../../ado/reference/ado-api/type-property-ado-stream.md) .  
  
-   Определите текущее состояние **потока** (закрытое, открытое или выполняемое) со свойством [State](../../../ado/reference/ado-api/state-property-ado.md) .  
  
-   Укажите режим доступа для **потока** со свойством [mode](../../../ado/reference/ado-api/mode-property-ado.md) .  
  
> [!NOTE]
>  URL-адреса, использующие схему HTTP, автоматически вызывают [поставщик OLE DB Майкрософт для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Объект **потока** является надежным для скриптов.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Stream](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Записи и потоки](../../../ado/guide/data/records-and-streams.md)
