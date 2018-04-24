---
title: Ссылающееся на библиотеки в приложении Visual Basic 6 ADO | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology: drivers
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual Basic application[ADO]
- ADO, libraries
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 20044ab8bc57f8c943a26457cd165d95afcd077f
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Ссылающееся на библиотеки ADO в приложение Visual Basic 6
В ADO библиотеки-импорт в приложение Microsoft Visual Basic 6, необходимо задать ссылку в проект Visual Basic.  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>Чтобы задать ссылки на библиотеки ADO в проекте Visual Basic  
  
1.  Создайте или откройте существующий проект Visual Basic.  
  
2.  Нажмите кнопку **проекта** пункт меню, а затем выберите **ссылки...**  с помощью раскрывающегося меню панели.  
  
3.  Из **доступные ссылки**, установите флажок для **Microsoft ActiveX Data Objects *n.n* библиотеки**, где ***n.n*** представляет последнюю версию номер версии. **Расположение** следующее поле необходимо определить, как выбор *$installDir\msado15.dll*, где *$installDir* — это путь к каталогу, в котором библиотека ADO была установлена.  
  
4.  Если вы планируете использовать ADO MD, повторите шаг 3, чтобы выбрать **Microsoft ActiveX Data Objects (многомерный) *n.n* библиотеки**. **Расположение** поля необходимо определить, как этот выбор *$installDir\msadomd.dll*.  
  
5.  Если вы планируете использовать ADOX, повторите шаг 3, чтобы выбрать **Microsoft ADO Ext. *n.n* DDL и безопасности**. **Расположение** поля необходимо определить, как этот выбор *$installDir\msadox.dll*.  
  
6.  Нажмите кнопку **ОК** для завершения настройки ссылки.  
  
## <a name="backward-compatibility"></a>Обратная совместимость  
 Установка ADO также копирует следующие библиотеки типов из более ранних версий:  
  
-   *msado27.tlb*, библиотека 2.7 тип ADO  
  
-   *msado26.tlb*, библиотека ADO 2.6 типов  
  
-   *msado25.tlb*, библиотека 2,5 тип ADO  
  
-   *msado21.tlb*, библиотека ADO 2.1 типов  
  
-   *msado20.tlb*, библиотека типов ADO 2.0  
  
 Если приложение должно использовать любой из этих библиотек ADO для обеспечения обратной совместимости, необходимо импортировать соответствующую версию библиотеки типов. Чтобы сделать это, выполните процедуры, описанные в предыдущем разделе, заменив *msado15.dll* по *msadoXX.tlb*, где *XX* представляет номер версии, необходимо импортировать.
