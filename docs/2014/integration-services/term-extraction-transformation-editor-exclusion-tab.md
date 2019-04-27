---
title: Редактор преобразования извлечения терминов (вкладка "исключение") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.inclusionexclusion.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 90110d95-fd97-4542-9cda-832c86606130
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c6292fa7798c9f9d76868b4230317eb99a1f8b3d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766287"
---
# <a name="term-extraction-transformation-editor-exclusion-tab"></a>Редактор преобразования «Извлечение терминов» (вкладка «Исключения»)
  Используйте вкладку **Исключение** в диалоговом окне **Редактор преобразования «Извлечение терминов»** для установки соединения с таблицей исключений и указания столбцов, в которых содержатся исключаемые термины.  
  
 Дополнительные сведения о преобразовании «Извлечения терминов» см. в разделе [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Использовать исключаемые термины**  
 Укажите, необходимо ли исключать определенные термины в процессе извлечения терминов, определив столбцы, содержащие исключаемые термины. Необходимо указать следующие свойства источника, если принято решение исключать термины.  
  
 **Диспетчер соединений OLE DB**  
 Выберите существующий диспетчер соединений OLE DB или создайте новое соединение, выбрав **Создать**.  
  
 **Создать**  
 Создайте новое соединение с базой данных, используя диалоговое окно **Настройка диспетчера соединений OLE DB** .  
  
 **Таблица или представление**  
 Выберите таблицу или представление, которое содержит исключаемые термины.  
  
 **Столбец**  
 Выберите столбец в таблице или представлении, который содержит исключаемые термины.  
  
 **Настройка вывода ошибок**  
 Используйте диалоговое окно [Настройка вывода ошибок](../../2014/integration-services/configure-error-output.md) для указания метода обработки ошибок для строк, вызвавших ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Извлечение терминов" (вкладка "Извлечение терминов")](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Редактор преобразования "Извлечение терминов" (вкладка "Дополнительно")](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md)   
 [Преобразование "Уточняющий запрос термина"](data-flow/transformations/lookup-transformation.md)  
  
  
