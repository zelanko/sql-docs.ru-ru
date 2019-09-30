---
title: Как изменить свойства экземпляра CDC | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8662905f72262cede8913c2a549cbca0df470875
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294712"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a>Как изменить свойства экземпляра CDC

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Следующая процедура описывает изменение свойств конфигурации экземпляра CDC с помощью консоли конструктора CDC.  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a>Изменение свойств конфигурации экземпляра CDC  
  
1.  В меню **Пуск** выберите **Консоль конструктора CDC**.  
  
2.  На панели слева разверните узел **Отслеживание измененных данных** , а затем разверните службу, содержащую экземпляр, свойства которого необходимо изменить.  
  
3.  Выберите имя экземпляра, свойства которого необходимо изменить.  
  
4.  На панели «Действия» с правой стороны консоли конструктора CDC щелкните **Свойства**.  
  
     Можно также щелкнуть правой кнопкой мыши экземпляр, свойства которого необходимо изменить, и выбрать команду **Свойства**.  
  
5.  В редакторе свойств измените свойства на следующих вкладках:  
  
    -   **Oracle**: на вкладке **Oracle** в редакторе свойств можно изменить описание, которое было введено на странице создания базы данных CDC мастера создания экземпляра, а также изменить данные для подключения к базе данных интеллектуального анализа журналов Oracle.  
  
         Сведения о том, что можно изменить на этой вкладке, приведены в разделе [Edit the Oracle Database Properties](../../integration-services/change-data-capture/edit-the-oracle-database-properties.md).  
  
    -   **Таблицы**: На вкладке **Таблицы** можно изменять таблицы и столбцы, выбранные в базе данных-источнике Oracle.  
  
         Сведения о том, что можно изменить на этой вкладке, приведены в разделе [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
    -   **Скрипты**: вкладка **Скрипты** служит для запуска или повторного запуска скрипта в базе данных-источнике Oracle, которая задает дополнительное журналирование.  
  
         Сведения о том, что можно сделать на этой вкладке, приведены в разделе [Review and Generate Supplemental Logging Scripts](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md).  
  
    -   **Дополнительно**: На вкладке **Дополнительно** можно добавлять особые свойства к экземпляру CDC.  
  
         Сведения о том, что можно сделать на этой вкладке, приведены в разделе [Edit the Advanced Properties](../../integration-services/change-data-capture/edit-the-advanced-properties.md).  
  
  
