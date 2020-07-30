---
title: Методы ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, methods
- methods [ADO]
ms.assetid: a38c5670-ba28-44f3-bd5b-fcb46880e904
author: rothja
ms.author: jroth
ms.openlocfilehash: a08f7c896b48f6cb76c9805d3bea9910a8f5bda8
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242864"
---
# <a name="ado-methods"></a>Методы ADO

|Метод|Описание|  
|-|-|  
|[Вызов](../../../ado/reference/ado-api/addnew-method-ado.md)|Создает новую запись для обновляемого объекта **набора записей** .|  
|[Добавить](../../../ado/reference/ado-api/append-method-ado.md)|Добавляет объект в коллекцию. Если коллекция является **полями**, то перед добавлением в коллекцию можно создать новый объект **поля** .|  
|[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)|Добавляет данные к большому текстовому или двоичному **полю**данных или к объекту **параметра** .|  
|[Примеры BeginTrans, CommitTrans и RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)|Управляет обработкой транзакций в объекте **соединения** следующим образом:<br /><br /> **Примеры BeginTrans** — начинает новую транзакцию.<br /><br /> **CommitTrans** — сохраняет все изменения и завершает текущую транзакцию. Она также может начать новую транзакцию.<br /><br /> **RollbackTrans** — отменяет все изменения и завершает текущую транзакцию. Она также может начать новую транзакцию.|  
|[Отмена](../../../ado/reference/ado-api/cancel-method-ado.md)|Отменяет выполнение ожидающего асинхронного вызова метода.|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Отменяет ожидающее пакетное обновление.|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Отменяет все изменения, внесенные в текущую или новую строку объекта **набора записей** , или коллекцию **полей** объекта **Record** перед вызовом метода **Update** .|  
|[Очистить](../../../ado/reference/ado-api/clear-method-ado.md)|Удаляет все объекты **Error** из коллекции **ошибок** .|  
|[Клонировать](../../../ado/reference/ado-api/clone-method-ado.md)|Создает дубликат объекта **набора записей** из существующего объекта **набора записей** . При необходимости указывает, что клон доступен только для чтения.|  
|[Закрыть](../../../ado/reference/ado-api/close-method-ado.md)|Закрывает открытый объект и все зависимые объекты.|  
|[CompareBookmarks](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)|Сравнивает две закладки и возвращает значение, указывающее на их относительные значения.|  
|[копирекорд](../../../ado/reference/ado-api/copyrecord-method-ado.md)|Копирует файл или каталог и его содержимое в другое расположение.|  
|[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)|Копирует указанное число символов или байтов (в зависимости от **типа**) в **потоке** в другой объект **потока** .|  
|[CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)|Создает новый объект **Parameter** с указанными свойствами.|  
|[Delete (Коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)|Удаляет объект из коллекции **параметров** .|  
|[Delete (коллекция полей ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)|Удаляет объект из коллекции **полей** .|  
|[Delete (набор записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Удаляет текущую запись или группу записей.|  
|[делетерекорд](../../../ado/reference/ado-api/deleterecord-method-ado.md)|Удаляет файл или каталог и все его подкаталоги.|  
|[Execute (команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|Выполняет запрос, инструкцию SQL или хранимую процедуру, указанную в свойстве **CommandText** .|  
|[Execute (подключение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|Выполняет указанный запрос, инструкцию SQL, хранимую процедуру или специфический для поставщика текст.|  
|[Поиск](../../../ado/reference/ado-api/find-method-ado.md)|Выполняет поиск в **наборе записей** для строки, удовлетворяющей заданным критериям.|  
|[Очистка](../../../ado/reference/ado-api/flush-method-ado.md)|Принудительно применяет содержимое **потока** , остающегося в буфере ADO, к базовому объекту, с которым связан **поток** .|  
|[Метод get_OLEDBCommand](../../../ado/reference/ado-api/get-oledbcommand-method.md)|Возвращает базовую команду OLEDB, сначала распространяюя все сведения о параметрах, заданные в команде ADO, в команду OLEDB.|  
|[GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)|Возвращает **набор записей** , строки которого представляют файлы и подкаталоги в каталоге, представленном этой **записью**.|  
|[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)|Возвращает все содержимое или часть содержимого большого текстового или двоичного объекта **поля** данных.|  
|[Метод GetDataProviderDSO](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Извлекает базовый объект источника данных OLEDB из поставщика фигур.|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Извлекает несколько записей объекта **набора записей** в массив.|  
|[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)|Возвращает **набор записей** в виде строки.|  
|[лоадфромфиле](../../../ado/reference/ado-api/loadfromfile-method-ado.md)|Загружает содержимое существующего файла в **поток**.|  
|[Перемещение](../../../ado/reference/ado-api/move-method-ado.md)|Перемещает текущую запись в объекте **набора записей** .|  
|[MoveFirst, MoveLast, MoveNext и MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Переходит к первой, последней, следующей или предыдущей записи в указанном объекте **набора записей** и делает запись текущей записью.|  
|[MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)|Перемещает файл или каталог и его содержимое в другое расположение.|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Очищает текущий объект **набора записей** и возвращает следующий **набор записей** путем перемещения по ряду команд.|  
|[Открыть (подключение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)|Открывает соединение с источником данных.|  
|[Открыть (запись ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|Открывает существующий объект **Record** или создает новый файл или каталог.|  
|[Open (набор записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Открывает курсор.|  
|[Открыть (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|Открывает объект **Stream** для управления потоками двоичных или текстовых данных.|  
|[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)|Получает сведения о схеме базы данных от поставщика.|  
|[Метод put_OLEDBCommand](../../../ado/reference/ado-api/put-oledbcommand-method.md)|Этот метод не выполняет никаких операций — он всегда возвращает S_OK.|  
|[Чтение](../../../ado/reference/ado-api/read-method.md)|Считывает указанное число байтов из объекта **потока** .|  
|[ReadText](../../../ado/reference/ado-api/readtext-method.md)|Считывает указанное число символов из объекта текстового **потока** .|  
|[Обновить](../../../ado/reference/ado-api/refresh-method-ado.md)|Обновляет объекты в коллекции, чтобы отразить объекты, доступные в поставщике, и связанные с ним.|  
|[Повтор](../../../ado/reference/ado-api/requery-method.md)|Обновляет данные в объекте **набора записей** путем повторного выполнения запроса, на котором основан объект.|  
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Обновляет данные в текущем объекте **набора записей** или коллекции **полей** объекта **записи** из базовой базы данных.|  
|[Сохранить](../../../ado/reference/ado-api/save-method.md)|Сохраняет **набор записей** в объекте File или **Stream** .|  
|[SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)|Сохраняет двоичное содержимое **потока** в файл.|  
|[Seek](../../../ado/reference/ado-api/seek-method.md)|Выполняет поиск индекса **набора записей** , чтобы быстро найти строку, совпадающую с указанными значениями, и изменяет положение текущей строки на эту строку.|  
|[сетеос](../../../ado/reference/ado-api/seteos-method.md)|Задает расположение, которое является концом потока.|  
|[скиплине](../../../ado/reference/ado-api/skipline-method.md)|Пропускает одну целую строку при чтении текстового потока.|  
|[STAT](../../../ado/reference/ado-api/stat-method.md)|Возвращает статистические сведения о открытом потоке.|  
|[Поддерживает](../../../ado/reference/ado-api/supports-method.md)|Определяет, поддерживает ли указанный объект **Recordset** определенный тип функциональности.|  
|[Обновление](../../../ado/reference/ado-api/update-method.md)|Сохраняет любые изменения, внесенные в текущую строку объекта **набора записей** , или коллекцию **Fields** объекта **Record** .|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Записывает все ожидающие пакетные обновления на диск.|  
|[Запись](../../../ado/reference/ado-api/write-method.md)|Записывает двоичные данные в объект **потока** .|  
|[WriteText](../../../ado/reference/ado-api/writetext-method.md)|Записывает указанную текстовую строку в объект **потока** .|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Перечислимые константы ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты и интерфейсы ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
