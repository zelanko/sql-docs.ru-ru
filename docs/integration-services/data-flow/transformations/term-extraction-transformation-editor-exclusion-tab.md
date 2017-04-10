---
title: "Редактор преобразования &#171;Извлечение терминов&#187; (вкладка &#171;Исключения&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.termextraction.inclusionexclusion.f1"
helpviewer_keywords: 
  - "редактор преобразования «Извлечение терминов»"
ms.assetid: 90110d95-fd97-4542-9cda-832c86606130
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Редактор преобразования &#171;Извлечение терминов&#187; (вкладка &#171;Исключения&#187;)
  Используйте вкладку **Исключение** в диалоговом окне **Редактор преобразования «Извлечение терминов»** для установки соединения с таблицей исключений и указания столбцов, в которых содержатся исключаемые термины.  
  
 Дополнительные сведения о преобразовании «Извлечения терминов» см. в разделе [Term Extraction Transformation](../../../integration-services/data-flow/transformations/term-extraction-transformation.md).  
  
## Параметры  
 **Использовать исключаемые термины**  
 Укажите, необходимо ли исключать определенные термины в процессе извлечения терминов, определив столбцы, содержащие исключаемые термины. Необходимо указать следующие свойства источника, если принято решение исключать термины.  
  
 **диспетчер соединений OLE DB**  
 Выберите существующий диспетчер соединений OLE DB или создайте новое соединение, выбрав **Создать**.  
  
 **Создать**  
 Создайте новое соединение с базой данных, используя диалоговое окно **Настройка диспетчера соединений OLE DB**.  
  
 **Таблица или представление**  
 Выберите таблицу или представление, которое содержит исключаемые термины.  
  
 **Столбец**  
 Выберите столбец в таблице или представлении, который содержит исключаемые термины.  
  
 **Настройка вывода ошибок**  
 Используйте диалоговое окно [Настройка вывода ошибок](../Topic/Configure%20Error%20Output.md) для указания метода обработки ошибок для строк, вызвавших ошибку.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Извлечение терминов" (вкладка "Извлечение терминов")](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Редактор преобразования "Извлечение терминов" (вкладка "Дополнительно")](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-advanced-tab.md)   
 [Преобразование «Уточняющий запрос термина»](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)  
  
  