---
title: UNION All Transformation Editor | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d9b8f598ce33a23370ff4a60ab0a13d6dba3ae5b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097309"
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
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Слияния данных с помощью Union All Transformation](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)   
 [Преобразование «Слияние»](data-flow/transformations/merge-transformation.md)   
 [Преобразование "Соединение слиянием"](data-flow/transformations/merge-join-transformation.md)  
  
  