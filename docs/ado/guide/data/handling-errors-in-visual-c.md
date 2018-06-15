---
title: Обработка ошибок в Visual C++ | Документы Microsoft
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
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68ce5fb8cc94b130de5171a45b65743e86eec3da
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271693"
---
# <a name="handling-errors-in-visual-c"></a>Обработка ошибок в Visual C++
В COM большинство операций возвращают код возврата HRESULT, указывающее, успешно ли выполнено функции. Директива #import приводит к возникновению ошибки кода программы-оболочки вокруг каждого «raw» метод или свойство и проверяет возвращенное значение HRESULT. Если значение HRESULT указывает на сбой, код программы-оболочки вызывает COM-ошибки путем вызова _com_issue_errorex() с кодом возврата HRESULT в качестве аргумента. Ошибка COM-объектов может быть перехвачена в **try-catch-** блока. (Catch ссылку на объект _com_error ради повышения его эффективности).  
  
 Помните, что они являются ошибками ADO: они являются результатом сбоя операции ADO. Базовый поставщик вернул ошибки отображаются в виде **ошибка** объекты в **подключения** объекта **ошибки** коллекции.  
  
 Директива #import создает только процедуры обработки ошибок для методов и свойств, объявленных в ADO DLL-файл. Тем не менее можно воспользоваться преимуществами такой же механизм обработки ошибок, написав собственные проверки ошибок макросу или встроенной функции. См. в разделе расширений Visual C++® примеры.
