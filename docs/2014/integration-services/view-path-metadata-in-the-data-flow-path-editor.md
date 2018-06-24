---
title: Просмотр метаданных пути в редакторе пути потока данных | Документы Microsoft
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
- metadata [Integration Services]
- paths [Integration Services], metadata
ms.assetid: 25cf8bdd-8691-4caa-96b6-3081b2f37dea
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4f775c2ee005b8f45f7a98c962ff1a8b6bb89649
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191015"
---
# <a name="view-path-metadata-in-the-data-flow-path-editor"></a>Просмотр метаданных пути в редакторе пути потока данных
  Пути соединяют два компонента потока данных. Чтобы просмотреть пути метаданных, поток данных должен содержать по крайней мере два соединенных компонента потока данных. Дополнительные сведения см. в разделах [Добавление или удаление компонента в потоке данных](data-flow/add-or-delete-a-component-in-a-data-flow.md) и [Соединение компонентов в потоке данных](data-flow/connect-components-in-a-data-flow.md).  
  
### <a name="to-view-path-metadata"></a>Просмотр метаданных пути  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Выберите вкладку **Поток данных** и дважды щелкните путь.  
  
4.  В диалоговом окне **Редактор пути потока данных** нажмите кнопку **Метаданные**.  
  
5.  Просмотрите метаданные пути, включая имена столбцов, тип данных, точность, масштаб, длину, кодовую страницу, а также имя исходного компонента каждого столбца.  
  
6.  Чтобы скопировать метаданные, нажмите кнопку **Копировать в буфер обмена**.  
  
7.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Пути служб Integration Services](data-flow/integration-services-paths.md)   
 [Поток данных](data-flow/data-flow.md)  
  
  