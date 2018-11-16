---
title: Выполнение добавочного поиска в активном документе | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 83abe7457afd480e275b8cb550ca12037b67d706
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643872"
---
# <a name="search-an-active-document-incrementally"></a>Выполнение добавочного поиска в активном документе
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В отдельном документе или окне можно осуществлять добавочный поиск с уточнением критериев путем ввода текста. При операции поиска первый набор символов, соответствующий введенным в ходе добавочного поиска в документе или окне, выделяется цветом. При добавочном поиске производится автоматический поиск во всем тексте документа или окна, кроме скрытого текста.  
  
 Для параметра **Учитывать регистр** во время добавочного поиска используется значение, заданное при предыдущем поиске. Например, если производился поиск в нескольких файлах с помощью диалогового окна **Поиск в файлах** при установленном флажке **Учитывать регистр**, а следующий поиск осуществляется добавочно, при этом поиске будет учитываться регистр.  
  
### <a name="to-search-incrementally"></a>Выполнение добавочного поиска  
  
1.  Откройте файл или окно, в котором требуется произвести поиск.  
  
2.  В меню **Правка** укажите **Дополнительно**, а затем **Добавочный поиск**.  
  
     Значок курсора примет форму бинокля со стрелкой, указывающей направление поиска, а в строке состояния появится надпись «Добавочный поиск».  
  
3.  Начинайте ввод строки текста.  
  
     В строке состояния отображается введенный текст, в то время как в редакторе первое совпадение этого текста выделяется цветом. По мере ввода редактор перемещается на следующее совпадение и выделяет его. Если совпадений текста не найдено, в строке состояния отображается следующее сообщение:  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 Добавочный поиск выполняется с текущей позиции в направлении конца документа слева направо. Добавочный поиск может быть запущен с помощью сочетания клавиш.  
  
> [!NOTE]  
>  Полный список сочетаний клавиш см. в статье [Сочетания клавиш среды SQL Server Management Studio](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
## <a name="see-also"></a>См. также:  
 [Поиск и замена](../../relational-databases/scripting/search-and-replace.md)   
 [осуществлять поиск в документах в интерактивном режиме](../../relational-databases/scripting/search-documents-interactively.md)   
 [Поиск документов с помощью списков результатов](../../relational-databases/scripting/search-documents-using-results-lists.md)   
 [Поиск текста с символами-шаблонами](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [Поиск текста с помощью регулярных выражений](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  
