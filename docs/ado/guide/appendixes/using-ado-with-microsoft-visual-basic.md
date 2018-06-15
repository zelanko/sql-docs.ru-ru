---
title: Использование ADO с помощью Microsoft Visual Basic | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, Visual Basic
- Visual Basic [ADO]
ms.assetid: 9dfb6784-037d-4f9d-bb7f-b506b4498573
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0250faf780229ec06c5fce38997bbf4eaf51cc43
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271303"
---
# <a name="using-ado-with-microsoft-visual-basic-and-visual-basic-for-applications"></a>Использование ADO с Microsoft Visual Basic и Visual Basic для приложений
Настройка проекта ADO и написание кода ADO аналогично ли вы использовать Visual Basic или Visual Basic для приложений. Этот раздел описывает, с помощью ADO в Visual Basic и Visual Basic для приложений и отмечает все различия.

## <a name="referencing-the-ado-library"></a>Ссылающаяся на библиотеку ADO
 Библиотека ADO должен ссылаться на проект.

#### <a name="to-reference-ado-from-microsoft-visual-basic"></a>Для ссылки ADO из Microsoft Visual Basic

1.  В Visual Basic из **проекта** последовательно выберите пункты **ссылок...** .

2.  Выберите **Microsoft ActiveX Data Objects x.x библиотеки** из списка. Убедитесь, что по крайней мере также выбираются следующие библиотеки:

    -   Visual Basic для приложений

    -   Объекты среды выполнения Visual Basic и процедуры

    -   Объекты Visual Basic и процедуры

    -   OLE-автоматизация

3.  Нажмите кнопку **ОК**.

 ADO можно использовать с Visual Basic для приложений, так же легко, или с помощью Microsoft Access, например.

#### <a name="to-reference-ado-from-microsoft-access"></a>Для ссылки ADO из Microsoft Access

1.  В Microsoft Access, выберите или создайте модуль из **модули** вкладке **базы данных** окна.

2.  На **средства** последовательно выберите пункты **ссылок...** .

3.  Выберите **Microsoft ActiveX Data Objects x.x библиотеки** из списка. Убедитесь, что по крайней мере также выбираются следующие библиотеки:

    -   Visual Basic для приложений

    -   Библиотека объектов Microsoft Access 8.0 (или более поздней версии)

    -   Библиотека объектов Microsoft DAO 3.5 (или более поздней версии)

4.  Нажмите кнопку **ОК**.

## <a name="creating-ado-objects-in-visual-basic"></a>Создание объектов ADO в Visual Basic
 Создание переменной службы автоматизации и экземпляр объекта для этой переменной можно использовать два метода: **Dim** или **CreateObject**.

### <a name="dim"></a>Dim
 Можно использовать **New** ключевого слова with **Dim** объявление и создание экземпляров объектов ADO за один шаг:

```
Dim conn As New ADODB.Connection
```

 Кроме того **Dim** оператор объявления и объекта при создании экземпляра также может быть два шага:

```
Dim conn As ADODB.Connection
Set conn = New ADODB.Connection
```

> [!NOTE]
>  Не требуется явно использовать `ADODB` progid с **Dim** инструкция, при условии, что правильно ссылка на библиотеку ADO в своем проекте. Тем не менее оно компенсируется, не будет конфликты имен с другими библиотеками.

> [!NOTE]
>  Например, при включении ссылки ADO и DAO в том же проекте, следует включать квалификатор, чтобы указать, какие объектной модели для использования при создании экземпляра **записей** объекты, как показано в следующем коде:

```
Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset
```

### <a name="createobject"></a>CreateObject
 С **CreateObject** создание экземпляра метода, объявление и объекта должны быть два отдельных этапа:

```
Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object
```

 Создание экземпляров объектов с **CreateObject** являются позднее связывание, что означает, что они не являются строго типизированными и завершение командной строки отключено. Однако его можно пропустить, ссылающаяся на библиотеку ADO из проекта и позволяет создавать экземпляры определенных версий объектов. Например:

```
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object
```

 Также может это сделать, в частности ссылку на библиотеку ADO версии 2.0 типа и создания объекта.

 Создание экземпляров объектов с помощью **CreateObject** обычно медленнее, чем использование метода **Dim** инструкции.

## <a name="handling-events"></a>Обработка событий
 Чтобы обработать события ADO в Visual Basic, необходимо объявить переменной уровня модуля с помощью **WithEvents** ключевое слово. Переменная может быть объявлен только как часть класса модуля и должен быть объявлен на уровне модуля. Более подробное описание обработки событий ADO, в разделе [обработка событий ADO](../../../ado/guide/data/handling-ado-events.md).

## <a name="visual-basic-examples"></a>Примеры Visual Basic
 Многие примеры Visual Basic входят в состав документации по ADO. Дополнительные сведения см. в разделе [примеры кода ADO в Visual Basic](../../../ado/reference/ado-api/ado-code-examples-in-visual-basic.md).

## <a name="see-also"></a>См. также
 [Объекты данных Microsoft ActiveX (ADO)](../../../ado/microsoft-activex-data-objects-ado.md) [использование ADO с Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) [использование ADO с языки сценариев](../../../ado/guide/appendixes/using-ado-with-scripting-languages.md)
