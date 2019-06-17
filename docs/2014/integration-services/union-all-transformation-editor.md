---
title: Объединение всех редактор преобразования | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b62fb5e33311f1011911c40fc858723b218bac55
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66054833"
---
# <a name="union-all-transformation-editor"></a>редактор преобразования «Объединить все»
  Для объединения нескольких входных наборов строк в один выходной набор строк используется диалоговое окно **Редактор преобразования «Объединить все»** . Включив преобразование «Объединить все» в поток данных, можно осуществлять слияние данных из нескольких потоков данных, создавать сложные наборы данных путем вложения преобразований «Объединить все» и повторно объединять строки после исправления ошибок данных.  
  
 Дополнительные сведения о преобразовании «Объединить все» см. в разделе [Union All Transformation](data-flow/transformations/union-all-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Имя выходного столбца**  
 Введите псевдоним для каждого столбца. По умолчанию, устанавливается имя входного столбца из первого (ссылочного) входного параметра, однако можно выбрать любое уникальное описательное имя.  
  
 **Вход 1 преобразования «Объединить все»**  
 Выберите из списка доступных входных столбцов в первом (ссылочном) входном параметре. Метаданные сопоставляемых столбцов должны совпадать.  
  
 **Вход n преобразования «Объединить все»**  
 Выберите из списка доступных входных столбцов во втором и дополнительных входных параметрах. Метаданные сопоставляемых столбцов должны совпадать.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Выполнение слияния данных с помощью преобразования «Объединить все»](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)   
 [Преобразование «Слияние»](data-flow/transformations/merge-transformation.md)   
 [Преобразование «Соединение слиянием»](data-flow/transformations/merge-join-transformation.md)  
  
  
