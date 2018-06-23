---
title: Редактор источника «ADO.NET» (страница «Вывод ошибок») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b47f60480938467fb8e618a0fa52b91449fafa54
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110215"
---
# <a name="ado-net-source-editor-error-output-page"></a>Редактор источника данных «ADO.NET» (страница «Вывод ошибок»)
  Страница **Вывод ошибок** диалогового окна **Редактор источника «ADO.NET»** используется для выбора параметров обработки ошибок, а также для установки свойств выходных столбцов ошибок.  
  
 Дополнительные сведения об источниках данных «ADO.NET» см. в разделе [ADO NET Source](data-flow/ado-net-source.md).  
  
 **Открытие страницы «Вывод ошибок»**  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий источник данных «ADO.NET».  
  
2.  На вкладке **Поток данных** дважды щелкните источник данных "ADO.NET".  
  
3.  В окне **Редактор источника «ADO.NET»** нажмите кнопку **Вывод ошибок**.  
  
## <a name="options"></a>Параметры  
 **Ввод-вывод**  
 Просмотр имени источника данных.  
  
 **Столбец**  
 Просмотрите внешние (исходные) столбцы, выбранные на странице **Диспетчер подключений** диалогового окна **Редактор источника "ADO.NET"** .  
  
 **Ошибка**  
 Задайте действие, которое необходимо выполнить при возникновении ошибки: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **См. также:** [Обработка ошибок в данных](data-flow/error-handling-in-data.md)  
  
 **Усечение**  
 Укажите, что нужно сделать при усечении: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Описание**  
 Просмотреть описание ошибки.  
  
 **Присвоить указанное значение выбранным ячейкам**  
 Укажите действие, которое необходимо применить ко всем выбранным ячейкам при возникновении ошибки или усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Применить**  
 Применить параметр обработки ошибок к выбранным ячейкам.  
  
## <a name="see-also"></a>См. также  
 [Редактор источника «ADO.NET» &#40;страницы диспетчера соединений&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md)   
 [Редактор источника «ADO.NET» &#40;страница «столбцы»&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md)   
 [Диспетчер подключений ADO.NET](connection-manager/ado-net-connection-manager.md)  
  
  