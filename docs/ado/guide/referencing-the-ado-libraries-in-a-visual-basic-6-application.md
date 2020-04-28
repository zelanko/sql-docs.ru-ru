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
ms.openlocfilehash: 25ea858995c884af202d3d80f4de675c9f4cda27
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923052"
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Ссылки на библиотеки ADO в приложении Visual Basic 6
Чтобы импортировать библиотеки ADO в приложение Microsoft Visual Basic 6, необходимо задать ссылку в проекте Visual Basic.  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>Установка ссылки на библиотеки ADO в проекте Visual Basic  
  
1.  Создайте новый или откройте существующий проект Visual Basic.  
  
2.  Щелкните элемент меню **проект** , а затем выберите **ссылки...** в раскрывающемся меню.  
  
3.  В поле **Доступные ссылки**установите флажок для **библиотеки Microsoft объекты данных ActiveX *n. n* **, где ***n. n*** представляет номер последней версии. В поле **Расположение** ниже следует выбрать *$installDir \msado15.dll*, где *$installDir* представляет путь к каталогу, в котором была установлена библиотека ADO.  
  
4.  Если вы планируете использовать объекты данных ActiveX (MD), повторите шаг 3, чтобы выбрать **библиотеку Microsoft объекты данных ActiveX (многомерная) *n. n* Library**. Поле **Location (расположение** ) должно обозначать этот выбор как *$installDir \мсадомд.длл*.  
  
5.  Если вы планируете использовать ADOX, повторите шаг 3, чтобы выбрать **Microsoft ADO ext. *n. n* для DDL и безопасности**. Поле **Location (расположение** ) должно обозначать этот выбор как *$installDir \мсадокс.длл*.  
  
6.  Нажмите кнопку **ОК** , чтобы завершить настройку ссылок.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 При установке ADO также копируются следующие библиотеки типов более ранних версий:  
  
-   *msado27. tlb*, Библиотека типов ADO 2,7  
  
-   *msado26. tlb*, Библиотека типов ADO 2,6  
  
-   *msado25. tlb*, Библиотека типов ADO 2,5  
  
-   *msado21. tlb*, Библиотека типов ADO 2,1  
  
-   *msado20. tlb*, Библиотека типов ADO 2,0  
  
 Если приложение должно использовать любую из этих библиотек ADO в целях обратной совместимости, необходимо импортировать соответствующую версию библиотеки типов. Для этого выполните процедуры, описанные в предыдущем разделе, заменив *Msado15. dll* на *мсадокскс. tlb*, где *XX* — номер версии, который необходимо импортировать.
