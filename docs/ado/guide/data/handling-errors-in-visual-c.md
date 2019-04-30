---
title: Обработка ошибок в Visual C++ | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e33d28201e1a2e4f7df8ac330ac89b3f00194b14
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161624"
---
# <a name="handling-errors-in-visual-c"></a>Обработка ошибок в Visual C++
В модели COM большинство операций возвращает код возврата HRESULT, указывающее, успешно ли завершен функции. Директива #import приводит к возникновению ошибки кода программы-оболочки вокруг каждого «raw» метод или свойство и проверяет возвращаемое значение HRESULT. Если значение HRESULT указывает на ошибку, код оболочки выводит ошибку COM, вызывающий _com_issue_errorex() с кодом возврата HRESULT в качестве аргумента. Ошибка COM-объектов может быть перехвачено в **try-catch** блока. (Catch ссылку на объект _com_error ради повышения эффективности в).  
  
 Помните, что ошибки ADO: они возникли: вследствие сбоя операции ADO. Отображаются ошибки, возвращенные базового поставщика как **ошибка** объекты в **подключения** объекта **ошибки** коллекции.  
  
 Директива #import создает только процедуры обработки ошибок для методов и свойств, объявленных в ADO DLL-файл. Тем не менее можно воспользоваться преимуществами такой же механизм обработки ошибок, написав собственные проверки ошибок макросу или встраиваемой функции. См. в разделе расширений Visual C++® примеры.
