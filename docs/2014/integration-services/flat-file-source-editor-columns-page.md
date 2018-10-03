---
title: Редактор исходного файла (страница "столбцы") с неструктурированными | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f65e6e5dd0561960c36eea953b39b71906981fa9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118734"
---
# <a name="flat-file-source-editor-columns-page"></a>Редактор источника «Неструктурированный файл» (страница «Столбцы»)
  С помощью узла **Столбцы** диалогового окна **Редактор источника "Неструктурированный файл"** можно сопоставлять выходной столбец с каждым внешним (исходным) столбцом.  
  
> [!NOTE]  
>  `FileNameColumnName` Свойство источника неструктурированного файла и `FastParse` его выходных столбцов недоступны в **Редактор источника неструктурированного файла**, однако его можно установить с помощью **расширенный редактор** . Дополнительные сведения об этих свойствах см. в подразделе «Источник "Неструктурированный файл"» раздела [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).  
  
 Дополнительные сведения об источнике «Неструктурированный файл» см. в разделе [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Параметры  
 **Доступные внешние столбцы**  
 Просмотр списка доступных внешних столбцов источника данных. В этой таблице нельзя добавлять или удалять столбцы.  
  
 **Внешний столбец**  
 Просмотр внешних (исходных) столбцов в том порядке, в котором их будет считывать задача. Этот порядок можно изменить, вначале очистив выделенные столбцы в таблице, а затем выбрав в списке внешние столбцы в другом порядке.  
  
 **Выходной столбец**  
 Введите уникальное имя для каждого выходного столбца. По умолчанию используется имя выбранного внешнего (исходного) столбца, однако можно выбрать любое уникальное описательное имя. Выбранное имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор источника «файл» с плоскими &#40;страницы диспетчера соединений&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md)   
 [Редактор источника «файл» с плоскими &#40;странице вывода ошибок&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Диспетчер подключений неструктурированных файлов](connection-manager/file-connection-manager.md)  
  
  
