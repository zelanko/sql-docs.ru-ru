---
title: 'Задача 3: Импорт значений домена из файла Excel | Документы Microsoft'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 242e8309-1195-495b-9cd5-aa127748c185
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fd5f73f95dce1d40689062a368e1cc222023541c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087035"
---
# <a name="task-3-importing-domain-values-from-an-excel-file"></a>Задача 3. Импорт значений домена из файла Excel
  При выполнении этой задачи вы импортируете значения для домена **Штат** из листа файла Excel.  
  
1.  Выберите домен **Штат** в **списке доменов**.  
  
2.  Убедитесь, что вкладка **Значения домена** активна в области справа.  
  
3.  В области справа щелкните **стрелку вниз** на панели инструментов рядом с кнопкой **Импортировать значения** и нажмите кнопку **Импорт допустимых значений из Excel**.  
  
     ![Импорт допустимых значений из меню Excel](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "Импорт допустимых значений из меню Excel")  
  
4.  Нажмите кнопку **Обзор**, выберите файл **Suppliers.xls**и нажмите кнопку **Открыть**.  
  
5.  Выберите значение **StatesToImport$** для параметра **Лист**.  
  
     ![Импорт домена значения диалоговое окно](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "Импорт домена значения диалоговое окно")  
  
6.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Импорт значений домена** . Должны появиться все названия штатов, импортированных в список. Обратите внимание, что флажок **Показать только новые** после импорта устанавливается автоматически. Если вы импортируете значения и не видите старых значений в списке, это вызвано тем, что указанный параметр автоматически включается после импорта. Чтобы увидеть все значения, снимите флажок. При повторном импорте набора значений ни одно из значений не будет импортировано, так как они уже есть в домене.  
  
     ![Показать только новые флажок на значения домена](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "Показывать только новые флажок на значения домена")  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 4. Задание правил домена](../../2014/tutorials/task-4-setting-domain-rules.md)  
  
  