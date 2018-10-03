---
title: Ссылки на библиотеки ADO в приложении Visual Basic 6 | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual Basic application[ADO]
- ADO, libraries
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8e37459c5e48fe817a3bdbb6a824550cf977f66
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696973"
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Ссылки на библиотеки ADO в приложении Visual Basic 6
Чтобы импортировать библиотеки ADO в приложении Microsoft Visual Basic 6, необходимо задать ссылку в проекте Visual Basic.  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>Чтобы задать ссылки на библиотеки ADO в проекте Visual Basic  
  
1.  Создайте новый или откройте существующий проект Visual Basic.  
  
2.  Нажмите кнопку **проекта** пункта меню, а затем выберите **ссылки...**  панели выберите в раскрывающемся меню.  
  
3.  Из **доступные ссылки**, установите флажок для **объектов данных Microsoft ActiveX *n.n* библиотеки**, где ***n.n*** представляет последнюю версию номер версии. **Расположение** следующее поле необходимо определить выбор в виде *$installDir\msado15.dll*, где *$installDir* — это путь к каталогу, в котором в библиотеке ADO установлено.  
  
4.  Если вы планируете использовать ADO MD, повторите шаг 3, чтобы выбрать **объектов данных Microsoft ActiveX (многомерные) *n.n* библиотеки**. **Расположение** поля необходимо определить этот выбор в виде *$installDir\msadomd.dll*.  
  
5.  Если вы планируете использовать ADOX, повторите шаг 3, чтобы выбрать **Microsoft ADO Ext. *n.n* DDL и безопасности**. **Расположение** поля необходимо определить этот выбор в виде *$installDir\msadox.dll*.  
  
6.  Нажмите кнопку **ОК** для завершения настройки ссылки.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Установка ADO также копирует следующие библиотеки типов из более ранних версий:  
  
-   *msado27.tlb*, библиотека 2.7 тип ADO  
  
-   *msado26.tlb*, библиотеку ADO 2.6 типов  
  
-   *msado25.tlb*, библиотека 2,5 тип ADO  
  
-   *msado21.tlb*, библиотека 2.1 тип ADO  
  
-   *msado20.tlb*, библиотека типов ADO 2.0  
  
 Если ваше приложение должно использовать любой из этих библиотек ADO для обеспечения обратной совместимости, необходимо импортировать соответствующую версию библиотеки типов. Чтобы сделать это, выполните процедуры, описанные в предыдущем разделе, заменив *msado15.dll* по *msadoXX.tlb*, где *XX* представляет номер версии, необходимо импортировать.
