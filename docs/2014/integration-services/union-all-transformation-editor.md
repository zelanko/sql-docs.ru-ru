---
title: Объединение всех редактор преобразования | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f34b73358bf9a268e4a2eef14f51800b0c9fea94
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138804"
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
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Объединение данных с помощью Union All Transformation](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)   
 [Преобразование «Слияние»](data-flow/transformations/merge-transformation.md)   
 [Преобразование "Соединение слиянием"](data-flow/transformations/merge-join-transformation.md)  
  
  
