---
title: "Плоский файл назначения | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 78a0ec526f83dcab8d7358ef5a51f1f6ccfd0a04
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="flat-file-destination"></a>назначение «Неструктурированный файл»
  Назначение «Неструктурированный файл» записывает данные в текстовый файл. Текстовый файл может быть в следующих форматах: с разделителями, фиксированной ширины, фиксированной ширины с разделителем строки и без выравнивания текста справа.  
  
 Можно настроить назначение «Неструктурированный файл» следующими способами:  
  
-   Предоставить блок текста, который вставлен в файл, прежде чем какие-либо данные будут записаны. Текст может предоставить необходимые сведения, такие как заголовки столбцов.  
  
-   Указать, нужно ли перезаписывать данные в файле назначения, имеющем то же имя.  
  
 Назначение использует диспетчер соединений с неструктурированными файлами для доступа к текстовым файлам. Путем установки свойств в диспетчере соединений с неструктурированными файлами, который использует назначение «Неструктурированный файл», можно определить способ, которым назначение «Неструктурированный файл» форматирует и записывает текстовый файл. При настройке диспетчера соединений с неструктурированными файлами указываются сведения о файле и о каждом столбце в файле. Например, указываются символы-разделители для столбцов и строк в файле, а также тип данных и длина каждого столбца. Дополнительные сведения см. в статье [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 Назначение "Неструктурированный файл" включает пользовательское свойство Header. Это свойство может быть обновлено выражением свойства при загрузке пакета. Дополнительные сведения см. в разделах [Выражения служб Integration Services (SSIS)](../../integration-services/expressions/integration-services-ssis-expressions.md), [Использование выражений свойств в пакетах](../../integration-services/expressions/use-property-expressions-in-packages.md) и [Пользовательские свойства неструктурированного файла](../../integration-services/data-flow/flat-file-custom-properties.md).  
  
 Этот назначение имеет один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-flat-file-destination"></a>Настройка назначения «Неструктурированный файл»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в диалоговом окне **Редактор источника «Неструктурированный файл»** , см. в следующих разделах:  
  
-   [Редактор назначения "Неструктурированный файл" (страница "Диспетчер соединений")](../../integration-services/data-flow/flat-file-destination-editor-connection-manager-page.md)  
  
-   [Редактор назначения "Неструктурированный файл" (страница "Сопоставления")](../../integration-services/data-flow/flat-file-destination-editor-mappings-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства неструктурированного файла](../../integration-services/data-flow/flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств для компонента потока данных см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Источник «Неструктурированный файл»](../../integration-services/data-flow/flat-file-source.md)   
 [Поток данных](../../integration-services/data-flow/data-flow.md)  
  
  
