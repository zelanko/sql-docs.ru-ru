---
title: "Адрес книги кнопки | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO], command buttons
- RDS scenarios [ADO], command buttons
ms.assetid: 80676831-6488-4dad-a558-c47c52256a22
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 31b0bb389b188c39b4590a774ac453a9de17fd56
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="address-book-command-buttons"></a>Адрес книги кнопки
Адресная книга приложение включает следующие кнопки:  
  
-   Объект **найти** кнопку, чтобы отправить запрос к базе данных.  
  
-   Объект **снимите** кнопку для очистки текстовые поля перед запуском нового поиска.  
  
-   **Обновить профиль** кнопку, чтобы сохранить изменения в записи о сотруднике.  
  
-   Объект **Отмена изменений** кнопку, чтобы отменить изменения.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="find-button"></a>Кнопка  
 Щелкнув **найти** кнопку активирует процедуру VBScript Find_OnClick Sub, которая создает и отправляет запрос SQL. При нажатии этой кнопки заполняет таблицу данных.  
  
## <a name="building-the-sql-query"></a>Создание SQL-запроса  
 Первая часть процедуры Find_OnClick Sub создает SQL-запроса одной фразе одновременно, путем добавления текстовых строк в глобальных инструкции SQL SELECT. Он начинается, установив переменную `myQuery` для инструкции SQL SELECT, которая запрашивает все строки данных из таблицы источника данных. Далее процедуры Sub сканирует каждого из четырех полей ввода на странице.  
  
 Так как программа использует слово `like` при построении инструкции SQL, запросы — поиск подстрок, а не точного совпадения.  
  
 Например если **Фамилия** поле содержится запись «Berge» и **заголовок** поле содержится запись «Руководитель программы», инструкции SQL (значение `myQuery`) читает:  
  
```  
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'  
```  
  
 При успешном выполнении запроса всех лиц с фамилией, содержащий текст «Berge» (например, Berge и Berger) и с заголовком, содержащих слова «Руководитель» (например, руководитель программы, дополнительные технологии) отображаются в сетке данных HTML.  
  
## <a name="preparing-and-sending-the-query"></a>Подготовка и отправка запроса  
 Последняя часть процедуры Find_OnClick Sub состоит из двух инструкций. Первый оператор назначает [SQL](../../../ado/reference/rds-api/sql-property.md) свойство [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) равное динамически построенного запроса SQL. Вторая инструкция вызывает **RDS. DataControl** объекта (`DC1`) для запроса к базе данных, а затем отображает результаты нового запроса в сетке.  
  
```  
Sub Find_OnClick  
   '...  
   DC1.SQL = myQuery  
   DC1.Refresh  
End Sub  
```  
  
## <a name="update-profile-button"></a>Кнопка «Обновить профиль»  
 Щелкнув **обновить профиль** процедуры VBScript Update_OnClick Sub, которая выполняет активирует кнопку [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта (`DC1`) [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) и [обновление](../../../ado/reference/rds-api/refresh-method-rds.md) методы.  
  
```  
Sub Update_OnClick  
   DC1.SubmitChanges  
   DC1.Refresh  
End Sub  
```  
  
 Когда `DC1.SubmitChanges` выполняет, пакеты сведения об обновлении удаленной службы данных и отправляет его на сервер по протоколу HTTP. Обновление отдельных; Если часть обновления завершается неудачно, никакие изменения выполняется и возвращается сообщение о состоянии. `DC1.Refresh`не является обязательным после **SubmitChanges** с удаленной службой данных, но это гарантирует свежими данными.  
  
## <a name="cancel-changes-button"></a>Кнопка "Отмена"  
 Щелкнув **Отмена изменений** активирует процедуру VBScript Cancel_OnClick Sub, который выполняет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта (`DC1)` [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) метод.  
  
```  
Sub Cancel_OnClick  
   DC1.CancelUpdate  
End Sub  
```  
  
 Когда `DC1.CancelUpdate` выполняется, он отклоняет все изменения, внесенные пользователем в записи о сотруднике в сетке данных с момента последнего запроса или обновления. Он восстанавливает исходные значения.  
  
## <a name="see-also"></a>См. также:  
 [Адрес книги кнопки навигации](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)   
 [Объект DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)



