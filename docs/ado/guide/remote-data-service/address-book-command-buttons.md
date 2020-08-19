---
description: Кнопки команд адресной книги
title: Кнопки для команд адресной книги | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2c2c3b0880a940b0f3388aced46c0cd9c888b786
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452336"
---
# <a name="address-book-command-buttons"></a>Кнопки команд адресной книги
Приложение адресной книги содержит следующие командные кнопки:  
  
-   Кнопка **поиска** для отправки запроса в базу данных.  
  
-   Кнопка **clear** для очистки текстовых полей перед началом нового поиска.  
  
-   Кнопка **обновления профиля** для сохранения изменений в записи сотрудника.  
  
-   Кнопка **отменить изменения** , чтобы отменить изменения.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="find-button"></a>Кнопка "найти"  
 Нажатие кнопки **найти** активирует процедуру VBScript Find_OnClick, которая создает и ОТПРАВЛЯЕТ запрос SQL. Нажатие этой кнопки заполняет сетку данных.  
  
## <a name="building-the-sql-query"></a>Создание SQL запроса  
 Первая часть Find_OnClick подпроцедуры создает SQL-запрос по одной фразе за раз, добавляя текстовые строки в глобальную инструкцию SQL SELECT. Он начинает с присвоения переменной `myQuery` инструкции SQL SELECT, которая запрашивает все строки данных из таблицы источника данных. Затем подпроцедура сканирует все четыре поля ввода на странице.  
  
 Поскольку программа использует слово `like` при построении инструкций SQL, запросы представляют собой поиск по подстрокам, а не точные совпадения.  
  
 Например, если в поле **Last Name (фамилия** ) содержится запись «Берже», а в поле « **Title** » содержится запись «руководитель программы», то инструкция SQL (значение `myQuery` ) будет считать следующее:  
  
```sql
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'  
```  
  
 Если запрос выполнен успешно, все лица с фамилией, содержащими текст «Берже» (например, «Берже» и «Бергер») и с заголовком, содержащим слова «руководитель программы» (например, «руководитель программы», «дополнительные технологии»), отображаются в сетке данных HTML.  
  
## <a name="preparing-and-sending-the-query"></a>Подготовка и отправка запроса  
 Последняя часть процедуры Find_OnClick состоит из двух операторов. Первая инструкция присваивает свойство [SQL](../../../ado/reference/rds-api/sql-property.md) [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) , равный динамически созданному SQL Query. Вторая инструкция вызывает **RDS. Объект элемента управления** ( `DC1` ) для запроса к базе данных, а затем отображение новых результатов запроса в сетке.  
  
```vb
Sub Find_OnClick  
   '...  
   DC1.SQL = myQuery  
   DC1.Refresh  
End Sub  
```  
  
## <a name="update-profile-button"></a>Кнопка обновления профиля  
 Нажатие кнопки **Обновить профиль** активирует процедуру VBScript Update_OnClick, которая выполняет [RDS. ](../../../ado/reference/rds-api/datacontrol-object-rds.md) `DC1` Методы [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) и [Refresh](../../../ado/reference/rds-api/refresh-method-rds.md) объекта элемента управления DataObject.  
  
```vb
Sub Update_OnClick  
   DC1.SubmitChanges  
   DC1.Refresh  
End Sub  
```  
  
 Когда `DC1.SubmitChanges` исполняется, служба удаленных данных упаковывает все сведения об обновлении и отправляет их на сервер по протоколу HTTP. Обновление — ALL или-Nothing; Если часть обновления завершается неудачно, никакие изменения не вносятся и возвращается сообщение о состоянии. `DC1.Refresh` не требуется после **SubmitChanges** с удаленной службой данных, но гарантирует актуальность данных.  
  
## <a name="cancel-changes-button"></a>Кнопка отмены изменений  
 Нажатие кнопки **Отмена изменений** активирует процедуру VBScript Cancel_OnClick, которая выполняет [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) `DC1)` [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) (метод.  
  
```vb
Sub Cancel_OnClick  
   DC1.CancelUpdate  
End Sub  
```  
  
 При `DC1.CancelUpdate` выполнении он отменяет любые изменения, внесенные пользователем в запись сотрудника в сетке данных с момента последнего запроса или обновления. Он восстанавливает исходные значения.  
  
## <a name="see-also"></a>См. также  
 [Кнопки навигации адресной книги](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)   
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)


