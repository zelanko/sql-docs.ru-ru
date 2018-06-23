---
title: Преобразования данных в другой тип данных используется преобразование «Конвертация данных» | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: bddfd8409bcca80a468638398270c7479e02d62f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094813"
---
# <a name="convert-data-to-a-different-data-type-by-using-the-data-conversion-transformation"></a>Преобразование данных в другой тип данных с помощью преобразования «Конвертация данных»
  Чтобы добавить и настроить преобразование «Конвертация данных», пакет должен обладать как минимум одной задачей потока данных и одним источником.  
  
### <a name="to-convert-data-to-a-different-data-type"></a>Произведение конвертации данных в другой тип данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Щелкните вкладку **Поток данных** и перетащите преобразование «Конвертация данных» из **области элементов**в область конструктора.  
  
4.  Подключите преобразование «Конвертация данных» к потоку данных, перетащив соединитель из источника или предыдущего преобразования в преобразование «Конвертация данных».  
  
5.  Дважды щелкните преобразование «Конвертация данных».  
  
6.  В диалоговом окне **Редактор преобразования "Конвертация данных"** в таблице **Доступные входные столбцы** установите флажки рядом со столбцами, данные из которых необходимо преобразовать.  
  
    > [!NOTE]  
    >  К каждому входному столбцу можно применить несколько преобразований.  
  
7.  При необходимости измените значение по умолчанию в столбце **Псевдоним вывода** .  
  
8.  Выберите новый тип данных для столбца из списка **Тип данных** . По умолчанию тип данных является типом данных входного столбца.  
  
9. Дополнительно, в зависимости от выбранного типа данных, можно обновить значения в столбцах **Длина**, **Точность**, **Масштаб**и **Кодовая страница** .  
  
10. Для настройки вывода ошибок нажмите **Настройка вывода ошибок**. Дополнительные сведения см. в разделе [Настройка вывода ошибок в компоненте потока данных](../../configure-an-error-output-in-a-data-flow-component.md).  
  
11. Нажмите кнопку **ОК**.  
  
12. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Преобразование «Конвертация данных»](data-conversion-transformation.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)   
 [Пути служб Integration Services](../integration-services-paths.md)   
 [Типы данных служб Integration Services](../integration-services-data-types.md)   
 [Задача потока данных] ((.. /.. /Control-Flow/Data-Flow-Task.MD)  
  
  