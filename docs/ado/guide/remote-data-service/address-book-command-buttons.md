---
title: Кнопки команд адресной книги | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO], command buttons
- RDS scenarios [ADO], command buttons
ms.assetid: 80676831-6488-4dad-a558-c47c52256a22
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d1aa5b628bec9399374b94a2cd78090207bf09b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922986"
---
# <a name="address-book-command-buttons"></a>Кнопки команд адресной книги
Адресная книга приложение включает в себя следующие кнопки:  
  
-   Объект **найти** кнопку, чтобы отправить запрос к базе данных.  
  
-   Объект **снимите** кнопку, чтобы очистить текстовые поля перед запуском нового поиска.  
  
-   **Обновить профиль** кнопку, чтобы сохранить изменения в записи о сотруднике.  
  
-   Объект **Отмена изменений** кнопку, чтобы отменить изменения.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="find-button"></a>Кнопка  
 Щелкнув **найти** кнопку активирует процедуры VBScript Find_OnClick Sub, которая создает и отправляет запрос SQL. После нажатия этой кнопки заполняет таблицу данных.  
  
## <a name="building-the-sql-query"></a>Создание SQL-запрос  
 Первая часть процедуры Find_OnClick Sub создает SQL-запрос, один фразой одновременно, путем добавления текстовых строк к глобальной инструкции SQL SELECT. Он начинается с настройки переменной `myQuery` в инструкцию SQL SELECT, который запрашивает все строки данных из таблицы источника данных. Далее процедуры Sub сканирует каждый из четырех полей ввода на странице.  
  
 Так как программа использует слово `like` в создании инструкций SQL, запросы, которые поиск подстрок, а не точные совпадения.  
  
 Например если **Фамилия** поле содержал запись «Berge» и **Title** поле содержал запись «Руководитель программы», инструкции SQL (значение `myQuery`) будет считывать:  
  
```sql
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'  
```  
  
 При успешном выполнении запроса всех лиц с фамилией, содержащее текст «Berge» (например Berge и Berger) и с заголовком, содержащих слова «Руководитель» (например, руководитель программы, передовыми технологиями), отображаются в сетке данных HTML.  
  
## <a name="preparing-and-sending-the-query"></a>Подготовка и отправка запроса  
 Последняя часть процедуры Find_OnClick Sub состоит из двух операторов. Первый оператор назначает [SQL](../../../ado/reference/rds-api/sql-property.md) свойство [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) равное динамически построенного запроса SQL. Вторая инструкция вызывает **RDS. DataControl** объекта (`DC1`) для запроса к базе данных, а затем отобразите новые результаты запроса в сетке.  
  
```vb
Sub Find_OnClick  
   '...  
   DC1.SQL = myQuery  
   DC1.Refresh  
End Sub  
```  
  
## <a name="update-profile-button"></a>Кнопки "обновить профиль"  
 Щелкнув **обновить профиль** процедуры VBScript Update_OnClick Sub, которая выполняет активирует кнопку [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта (`DC1`) [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) и [обновить](../../../ado/reference/rds-api/refresh-method-rds.md) методы.  
  
```vb
Sub Update_OnClick  
   DC1.SubmitChanges  
   DC1.Refresh  
End Sub  
```  
  
 Когда `DC1.SubmitChanges` выполняет, удаленной службы данных упаковывает все сведения об обновлении и отправляет их на сервер по протоколу HTTP. Обновление отдельных; Если в ходе обновления завершится неудачно, ни одно из изменений выполняется и возвращается сообщение об изменении состояния. `DC1.Refresh` Нет необходимости после **SubmitChanges** с удаленной службой данных, но он обеспечивает новые данные.  
  
## <a name="cancel-changes-button"></a>Кнопка "Отмена изменений"  
 Щелкнув **Отмена изменений** активирует процедуру VBScript Cancel_OnClick Sub, выполняющий [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта (`DC1)` [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) метод.  
  
```vb
Sub Cancel_OnClick  
   DC1.CancelUpdate  
End Sub  
```  
  
 Когда `DC1.CancelUpdate` выполняет, он отклоняет все изменения, внесенные пользователем в записи о сотруднике в сетке данных с момента последнего запроса или обновления. Он восстанавливает исходные значения.  
  
## <a name="see-also"></a>См. также  
 [Кнопки навигации адресной книги](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)   
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)


