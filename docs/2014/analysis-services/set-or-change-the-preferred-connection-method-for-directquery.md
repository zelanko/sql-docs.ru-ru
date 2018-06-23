---
title: Установка или Изменение предпочтительного метода подключения для DirectQuery | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf6abf3e4576fb28155529ee1bdfd24520176010
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192760"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a>Установка или изменение предпочтительного метода подключения для DirectQuery
  При создании модели для использования в режиме DirectQuery необходимо сначала настроить поддержку DirectQuery в среде конструирования. Чтобы сделать это, в разделе [Включение режима разработки DirectQuery &#40;табличные службы SSAS&#41;](tabular-models/enable-directquery-mode-in-ssdt.md).  
  
 Когда все готово к развертыванию модели, необходимо настроить некоторые дополнительные свойства, обеспечивающие доступ пользователей к модели с помощью одного из режимов DirectQuery:  
  
-   Необходимо указать, какие данные должны использоваться в запросах к модели: кэшированные или из реляционного источника данных. Можно использовать только DirectQuery или гибридный режим.  
  
-   Если используются разделы, следует указать, какой раздел будет использоваться в качестве источника данных DirectQuery.  
  
-   Необходимо настроить параметры олицетворения для пользователей, которым необходим доступ к источнику данных SQL Server.  
  
 Эта процедура описывает, как в конструкторе настраивается предпочтительный метод подключения для модели DirectQuery. Кроме того, описывается изменение этого свойства в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] после развертывания модели.  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a>Настройка предпочтительного метода подключения для модели DirectQuery  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], откройте файл решения для модели DirectQuery.  
  
2.  В Visual Studio в меню **Проект** выберите пункт **Свойства**.  
  
3.  На панели **Свойства** задайте для свойства **DirectQueryMode**одно из значений, обеспечивающих использование DirectQuery:  
  
    -   **InMemory с DirectQuery**— с этим параметром модель развертывается, но необходимо обработать кэш, прежде чем к ней можно будет выполнять запросы.  
  
    -   **DirectQuery с InMemory**— с этим параметром кэш будет доступен для клиентов, если он уже обработан. Если выполнить развертывание модели с этим параметром и не обработать кэш, у некоторых клиентов при попытке подключения к модели будет возникать ошибка.  
  
    -   **Только DirectQuery**— с этим параметром метаданные развертываются, но в модели нет данных. Клиенты, пытающиеся подключиться в режиме In-Memory, будут получать ошибку, указывающую, что модель не существует или не обработана.  
  
4.  При наличии ошибок откройте в Visual Studio **Список ошибок** и решите проблемы, мешающие развернуть модель в режиме DirectQuery.  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a>Проверка или изменение предпочтительного метода подключения для модели DirectQuery  
  
1.  В [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру с развернутой моделью DirectQuery.  
  
2.  Щелкните правой кнопкой мыши шаблон базы данных и выберите пункт **Свойства**.  
  
3.  На панели **Свойства** задайте для свойства **DirectQueryMode**одно из следующих значений:  
  
    -   **Только DirectQuery**  
  
    -   **InMemory с DirectQuery**  
  
    -   **DirectQuery с InMemory**  
  
 Обратите внимание: это те же свойства, что задавались в проекте перед развертыванием в Visual Studio. Изменить предпочтительный режим подключения для режима DirectQuery можно в любое время при условии, что модель настроена на использование DirectQuery.  
  
## <a name="see-also"></a>См. также  
 [Режим DirectQuery (табличные службы SSAS)](tabular-models/directquery-mode-ssas-tabular.md)   
 [Включить режим разработки DirectQuery &#40;табличные службы SSAS&#41;](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  