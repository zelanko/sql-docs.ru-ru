---
title: Использование заметок в пакетах | Документы Майкрософт
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
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f00ac9f1013bbf9b95999f51631970f9935364c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100226"
---
# <a name="use-annotations-in-packages"></a>Использование заметок в пакетах
  Конструктор служб [!INCLUDE[ssIS](../includes/ssis-md.md)] предоставляет заметки, которые можно использовать для обеспечения самодокументируемости пакетов, упрощения их понимания и поддержки. Заметки вы можете добавлять в области конструктора потока управления, потока данных и обработчика событий конструктора [!INCLUDE[ssIS](../includes/ssis-md.md)] . Заметки могут содержать разные типы текста; они полезны при добавлении меток, примечаний и других описательных сведений в пакет. Создание заметок возможно только во время проектирования. Например, они не записываются в журналы.  
  
 При нажатии клавиши ВВОД текст переносится на следующую строку. Размер поля заметки автоматически увеличивается по мере добавления дополнительных строк текста. Заметки пакета сохраняются в виде обычного текста в разделе CDATA файла пакета.  
  
 Дополнительные сведения об изменении формата файла пакета см. в разделе [Формат пакетов служб SSIS](../../2014/integration-services/ssis-package-format.md).  
  
 При сохранении пакета конструктор служб [!INCLUDE[ssIS](../includes/ssis-md.md)] сохраняет включенные в пакет заметки.  
  
### <a name="to-add-an-annotation-to-a-package"></a>Добавление заметки к пакету  
  
-   [Добавление заметки к пакету](../../2014/integration-services/add-an-annotation-to-a-package.md)  
  
  