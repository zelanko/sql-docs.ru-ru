---
title: Использование ADO с Microsoft Visual Basic | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, Visual Basic
- Visual Basic [ADO]
ms.assetid: 9dfb6784-037d-4f9d-bb7f-b506b4498573
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: abbdbeec81a029716ac6516f9436373e91365a23
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702775"
---
# <a name="using-ado-with-microsoft-visual-basic-and-visual-basic-for-applications"></a>Использование ADO с Microsoft Visual Basic и Visual Basic для приложений
Настройка в проект ADO и написания кода ADO аналогично ли вы использовать Visual Basic или Visual Basic для приложений. Этот раздел описывает, с помощью ADO в Visual Basic и Visual Basic для приложений и отмечает все различия.

## <a name="referencing-the-ado-library"></a>Ссылки на библиотеки ADO
 Проект должен ссылаться на библиотеки ADO.

#### <a name="to-reference-ado-from-microsoft-visual-basic"></a>Для ссылки на ADO с Microsoft Visual Basic

1.  В Visual Basic из **проекта** меню, выберите **ссылки...** .

2.  Выберите **x.x объектов данных Microsoft ActiveX библиотеки** из списка. Убедитесь, что по крайней мере также выбираются следующие библиотеки:

    -   Visual Basic для приложений

    -   Объекты среды выполнения Visual Basic и процедуры

    -   Объекты Visual Basic и процедуры

    -   OLE-автоматизация

3.  Нажмите кнопку **ОК**.

 ADO можно использовать с Visual Basic для приложений, так же легко, или с помощью Microsoft Access, например.

#### <a name="to-reference-ado-from-microsoft-access"></a>Для ссылки ADO из Microsoft Access

1.  В Microsoft Access, выберите или создайте модуль из **модули** вкладке **базы данных** окна.

2.  На **средства** меню, выберите **ссылки...** .

3.  Выберите **x.x объектов данных Microsoft ActiveX библиотеки** из списка. Убедитесь, что по крайней мере также выбираются следующие библиотеки:

    -   Visual Basic для приложений

    -   Библиотека объектов Microsoft Access 8.0 (или более поздней версии)

    -   Библиотека объектов Microsoft DAO 3.5 (или более поздней версии)

4.  Нажмите кнопку **ОК**.

## <a name="creating-ado-objects-in-visual-basic"></a>Создание объектов ADO в Visual Basic
 Чтобы создать переменную службы автоматизации и экземпляр объекта для этой переменной, можно использовать два метода: **DIM** или **CreateObject**.

### <a name="dim"></a>Dim
 Можно использовать **New** ключевого слова with **Dim** объявления и создания экземпляров объектов ADO за один шаг:

```
Dim conn As New ADODB.Connection
```

 Кроме того **Dim** оператор объявления и объекта при создании экземпляра также может быть два этапа:

```
Dim conn As ADODB.Connection
Set conn = New ADODB.Connection
```

> [!NOTE]
>  Не требуется явным образом использовать `ADODB` progid с **Dim** инструкция, при условии, что правильно ссылка на библиотеки ADO в проекте. Тем не менее с его помощью гарантирует, что не нужно предотвратить конфликты имен с другими библиотеками.

> [!NOTE]
>  Например, при включении ссылки на ADO и DAO в том же проекте, следует включать квалификатор, чтобы указать, какие объектной модели для использования при создании экземпляра **записей** объекты, как показано в следующем коде:

```
Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset
```

### <a name="createobject"></a>CreateObject
 С помощью **CreateObject** метод, объявление и объекта при создании экземпляра должно быть два отдельных этапа:

```
Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object
```

 Создание экземпляров объектов с **CreateObject** происходят с поздним связыванием, что означает, что они не являются строго типизированными и командной строки завершение отключено. Тем не менее он позволяет пропустить ссылки на библиотеки ADO из проекта и позволяет создавать экземпляры конкретных версий объектов. Пример:

```
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object
```

 Также может это сделать, в частности Создание ссылки на библиотеки ADO версии 2.0 типов и создания объекта.

 Создание экземпляров объектов с помощью **CreateObject** обычно медленнее, чем использование метода **Dim** инструкции.

## <a name="handling-events"></a>Обработка событий
 Для обработки событий ADO в Microsoft Visual Basic, необходимо объявить переменной уровня модуля с помощью **WithEvents** ключевое слово. Переменную можно объявить только как часть класса модуля и должен быть объявлен на уровне модуля. Более подробное описание того, обработка событий ADO, см. в разделе [обработка событий ADO](../../../ado/guide/data/handling-ado-events.md).

## <a name="visual-basic-examples"></a>Примеры Visual Basic
 Многие примеры Visual Basic входят в состав документации по объектам ADO. Дополнительные сведения см. в разделе [примеры кода ADO в Microsoft Visual Basic](../../../ado/reference/ado-api/ado-code-examples-in-visual-basic.md).

## <a name="see-also"></a>См. также
 [Объекты данных Microsoft ActiveX (ADO)](../../../ado/microsoft-activex-data-objects-ado.md) [использование объектов ADO с Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) [использование объектов ADO с языками сценариев](../../../ado/guide/appendixes/using-ado-with-scripting-languages.md)
