---
title: Редактор источника "Неструктурированный файл" (страница "столбцы") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 5f882aae9062d97914c86644a7be0ea126ed9dd8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966444"
---
# <a name="flat-file-source-editor-columns-page"></a>Редактор источника «Неструктурированный файл» (страница «Столбцы»)
  С помощью узла **Столбцы** диалогового окна **Редактор источника "Неструктурированный файл"** можно сопоставлять выходной столбец с каждым внешним (исходным) столбцом.  
  
> [!NOTE]  
>  `FileNameColumnName`Свойство источника "Неструктурированный файл" и `FastParse` свойство его выходных столбцов недоступны в **редакторе источника "Неструктурированный файл**", но могут быть заданы с помощью **Расширенный редактор**. Дополнительные сведения об этих свойствах см. в подразделе «Источник "Неструктурированный файл"» раздела [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).  
  
 Дополнительные сведения об источнике «Неструктурированный файл» см. в разделе [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Варианты  
 **Доступные внешние столбцы**  
 Просмотр списка доступных внешних столбцов источника данных. В этой таблице нельзя добавлять или удалять столбцы.  
  
 **Внешний столбец**  
 Просмотр внешних (исходных) столбцов в том порядке, в котором их будет считывать задача. Этот порядок можно изменить, вначале очистив выделенные столбцы в таблице, а затем выбрав в списке внешние столбцы в другом порядке.  
  
 **Выходной столбец**  
 Введите уникальное имя для каждого выходного столбца. По умолчанию используется имя выбранного внешнего (исходного) столбца, однако можно выбрать любое уникальное описательное имя. Выбранное имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор источника "Неструктурированный файл" &#40;страница "Диспетчер соединений"&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md)   
 [Редактор источника "Неструктурированный файл" &#40;страница "вывод ошибок"&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Диспетчер соединений с неструктурированными файлами](connection-manager/file-connection-manager.md)  
  
  
