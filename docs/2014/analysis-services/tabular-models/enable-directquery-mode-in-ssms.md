---
title: Настройте в памяти или доступа DirectQuery для базы данных табличной модели | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c91dd8529fa6ddfb111ebb87cb84d87a55d3a709
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192757"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>Настройка доступа в памяти или доступа DirectQuery для базы данных табличной модели
  В этом разделе описано, как изменить свойства подключения уже развернутой табличной модели, чтобы ее можно было использовать в режиме прямого запроса (Direct Query).  
  
 Дополнительные сведения об этих свойствах и конфигурации для наиболее распространенных сценариев см. в разделе [сценарии развертывания DirectQuery &#40;табличные службы SSAS&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
## <a name="requirements"></a>Требования  
 Включение использования режима Direct Query — это многоступенчатый процесс. Необходимо сделать следующее:  
  
1.  убедиться в том, что модель не имеет функций, которые могут вызвать ошибки при проверке в режиме Direct Query;  
  
2.  изменить режим хранения для модели для поддержки режима Direct Query;  
  
3.  развернуть модель в режиме, который поддерживает запросы как в гибридном, так и чистом режиме Direct Query;  
  
4.  изменить строку подключения развернутой базы данных для поддержки режима Direct Query.  
  
 Предполагается, что модель уже создана и проверена и требуется только обеспечить доступ в режиме Direct Query с такого клиента, как [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a>Изменение свойств строки подключения для модели  
  
1.  В среде SQL Server Management Studio откройте экземпляр, на котором развернута модель.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши имя базы данных, модели и выберите **свойства**.  
  
3.  Найдите свойство **DirectQueryMode**. Чтобы включить использование реляционного источника данных, это свойство должно иметь одно из следующих значений.  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  