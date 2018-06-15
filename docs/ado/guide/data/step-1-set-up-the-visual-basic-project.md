---
title: 'Шаг 1: Настройка проекта Visual Basic | Документы Microsoft'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eeecb16bd73df86dfdd40013b0a01cd8f90947ff
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272863"
---
# <a name="step-1-set-up-the-visual-basic-project"></a>Шаг 1: Настройка проекта Visual Basic
В этом сценарии предполагается наличие Microsoft Visual Basic 6.0, поставщик Microsoft OLE DB и ADO 2.5 или более поздней версии для публикаций в Интернете на компьютере. Будет сначала создайте новый проект и затем добавлять некоторые элементы управления в форму по умолчанию в проекте.  
  
### <a name="to-create-an-ado-project"></a>Чтобы создать проект ADO:  
  
1.  В Visual Basic, создайте новый проект стандартного исполняемого файла.  
  
2.  В меню «Проект» выберите ссылки.  
  
3.  Выберите «Microsoft ActiveX данных объектов 2.5 библиотека» и нажмите кнопку ОК.  
  
### <a name="to-insert-controls-on-the-main-form"></a>Вставка элементов управления в форме:  
  
1.  Добавьте элемент управления ListBox в форму Form1. Значение свойства Name **lstMain**.  
  
2.  Добавьте другой элемент управления ListBox в форму Form1. Значение свойства Name **lstDetails**.  
  
3.  Добавьте элемент управления TextBox в форму Form1. Значение свойства Name **txtDetails**.  
  
## <a name="see-also"></a>См. также  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 2. Инициализация главного списка](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)
