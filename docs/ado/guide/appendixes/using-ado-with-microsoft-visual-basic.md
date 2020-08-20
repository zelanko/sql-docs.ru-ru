---
description: Использование ADO с Microsoft Visual Basic и Visual Basic для приложений
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b4e8304204a6eaebf6b64d5cb9ad44e5fa1602da
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454016"
---
# <a name="using-ado-with-microsoft-visual-basic-and-visual-basic-for-applications"></a>Использование ADO с Microsoft Visual Basic и Visual Basic для приложений
Настройка проекта ADO и написание кода ADO похожи на то, используется ли Visual Basic или Visual Basic для приложений. В этом разделе рассматривается использование ADO с Visual Basic и Visual Basic для приложений и примечаниями.

## <a name="referencing-the-ado-library"></a>Ссылка на библиотеку ADO
 Проект должен ссылаться на библиотеку ADO.

#### <a name="to-reference-ado-from-microsoft-visual-basic"></a>Ссылка на ADO из Microsoft Visual Basic

1.  В Visual Basic в меню **проект** выберите **ссылки...**.

2.  Выберите **библиотеку Microsoft объекты данных ActiveX x. x** из списка. Убедитесь, что выбраны по крайней мере следующие библиотеки:

    -   Visual Basic для приложений

    -   Объекты и процедуры среды выполнения Visual Basic

    -   Объекты и процедуры Visual Basic

    -   OLE-автоматизация

3.  Нажмите кнопку **ОК**.

 ADO можно использовать так же просто, как Visual Basic для приложений с помощью Microsoft Access, например.

#### <a name="to-reference-ado-from-microsoft-access"></a>Обращение к ADO из Microsoft Access

1.  В Microsoft Access выберите или создайте модуль на вкладке **модули** в окне **базы данных** .

2.  В меню **Сервис** выберите **ссылки...**.

3.  Выберите **библиотеку Microsoft объекты данных ActiveX x. x** из списка. Убедитесь, что выбраны по крайней мере следующие библиотеки:

    -   Visual Basic для приложений

    -   Библиотека объектов Microsoft Access 8,0 (или более поздней версии)

    -   Библиотека объектов Microsoft DAO 3,5 (или более поздней версии)

4.  Нажмите кнопку **ОК**.

## <a name="creating-ado-objects-in-visual-basic"></a>Создание объектов ADO в Visual Basic
 Чтобы создать переменную автоматизации и экземпляр объекта для этой переменной, можно использовать два метода: **Dim** или **CreateObject**.

### <a name="dim"></a>Dim
 Ключевое слово **New** можно использовать с **Dim** для объявления и создания экземпляров объектов ADO за один шаг:

```
Dim conn As New ADODB.Connection
```

 Кроме того, объявление оператора **Dim** и создание экземпляра объекта также могут быть двумя шагами:

```
Dim conn As ADODB.Connection
Set conn = New ADODB.Connection
```

> [!NOTE]
>  Не обязательно явно использовать `ADODB` ProgID с инструкцией **Dim** , если вы правильно ссылались на библиотеку ADO в проекте. Однако его использование гарантирует, что имена не будут конфликтовать с другими библиотеками.

> [!NOTE]
>  Например, если вы включили в один проект ссылки на ADO и DAO, необходимо включить квалификатор, указывающий, какую объектную модель использовать при создании экземпляров объектов **набора записей** , как показано в следующем коде:

```
Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset
```

### <a name="createobject"></a>CreateObject
 При использовании метода **CreateObject** объявление и создание экземпляра объекта должны быть двух дискретных шагов:

```
Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object
```

 Объекты, созданные с помощью **CreateObject** , имеют позднюю привязку, что означает, что они не являются строго типизированными, а завершение командной строки отключено. Однако он позволяет пропустить ссылку на библиотеку ADO из проекта и позволяет создавать экземпляры конкретных версий объектов. Например:

```
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object
```

 Это можно также сделать, специально создав ссылку на библиотеку типов ADO версии 2,0 и создав объект.

 Создание экземпляров объектов с помощью метода **CreateObject** обычно выполняется медленнее, чем при использовании оператора **Dim** .

## <a name="handling-events"></a>Обработка событий
 Чтобы обеспечить обработку событий ADO в Microsoft Visual Basic, необходимо объявить переменную уровня модуля с помощью ключевого слова **WithEvents** . Переменная может быть объявлена только как часть модуля класса и должна быть объявлена на уровне модуля. Более подробное описание обработки событий ADO см. в разделе [Обработка событий ADO](../../../ado/guide/data/handling-ado-events.md).

## <a name="visual-basic-examples"></a>Примеры Visual Basic
 Многие примеры Visual Basic включены в документацию по ADO. Дополнительные сведения см. [в статье примеры кода ADO в Microsoft Visual Basic](../../../ado/reference/ado-api/ado-code-examples-in-visual-basic.md).

## <a name="see-also"></a>См. также:
 [Microsoft объекты данных ActiveX (ADO)](../../../ado/microsoft-activex-data-objects-ado.md) с [помощью ADO и Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) [Использование ADO с языками сценариев](../../../ado/guide/appendixes/using-ado-with-scripting-languages.md)
