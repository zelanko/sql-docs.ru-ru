---
title: Редактор преобразования "Копирование столбца" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03d8cdb35372ed9850f3329f26e2647e018d9583
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66060294"
---
# <a name="copy-column-transformation-editor"></a>редактор преобразования «Копирование столбца»
  Диалоговое окно **Редактор преобразования «Копирование столбцов»** используется для выбора копируемых столбцов и присвоения имен новым выходным столбцам.  
  
 Дополнительные сведения о редакторе преобразований «Копирование столбцов» см. в разделе [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md).  
  
> [!NOTE]  
>  При простом копировании всех данных из источника в назначение использовать преобразование «Копирование столбцов» необязательно. В некоторых ситуациях можно напрямую соединить источник с назначением, если преобразование данных не требуется. В некоторых ситуациях часто бывает предпочтительнее использовать мастер импорта и экспорта SQL Server, который создаст пакет. Позже пакет можно расширить и изменить его конфигурацию. Дополнительные сведения см. в разделе [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Выберите копируемые столбцы с помощью флажков. Выбранные столбцы добавляются в качестве входных столбцов в таблицу, представленную ниже.  
  
 **Входной столбец**  
 Выберите столбцы для копирования из списка доступных входных столбцов. Выбранные столбцы обозначаются флажками в таблице **Доступные входные столбцы** .  
  
 **Псевдоним вывода**  
 Введите псевдоним для каждого нового выходного столбца. По умолчанию, используется **Копия**и далее имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
