---
title: Редактор назначения «ODBC» (страница «вывод ошибок») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.errorhandling.f1
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 82853123767237314edac1e301723724628439d9
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965044"
---
# <a name="odbc-destination-editor-error-output-page"></a>Редактор назначения «ODBC» (страница «Вывод ошибок»)
  Страница **Вывод ошибок** диалогового окна **Редактор назначения ODBC** используется для выбора параметров обработки ошибок.  
  
 Дополнительные сведения о назначении ODBC см. в разделе [ODBC Destination](data-flow/odbc-destination.md).  
  
 **Открытие страницы «Вывод ошибок» редактора назначения ODBC**  
  
## <a name="task-list"></a>Список задач  
  
-   В среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]откройте пакет служб [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] , содержащий назначение ODBC.  
  
-   На вкладке **Поток данных** дважды щелкните назначение ODBC.  
  
-   В окне **Редактор назначения ODBC**нажмите кнопку **Вывод ошибок**.  
  
## <a name="options"></a>Варианты  
  
### <a name="inputoutput"></a>Ввод-вывод  
 Просмотр имени источника данных.  
  
### <a name="column"></a>Столбец  
 Не используется.  
  
### <a name="error"></a>Error  
 Выберите порядок обработки ошибок в потоке назначением ODBC: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
### <a name="truncation"></a>Усечение  
 Выберите порядок обработки усечений в потоке назначением ODBC: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
### <a name="description"></a>Описание  
 Просмотрите описание ошибки.  
  
### <a name="set-this-value-to-selected-cells"></a>Присвоить указанное значение выбранным ячейкам  
 Выберите, как назначение ODBC обрабатывает все выбранные ячейки при возникновении ошибки или усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
### <a name="apply"></a>Применить  
 Примените параметры обработки ошибок к выбранным ячейкам.  
  
## <a name="error-handling-options"></a>Параметры обработки ошибок  
 Следующие параметры позволяют настроить обработку ошибок и усечений назначением ODBC.  
  
### <a name="fail-component"></a>Компонент, завершившийся сбоем  
 Задача потока данных заканчивается сбоем, если возникли ошибка или усечение. Это поведение установлено по умолчанию.  
  
### <a name="ignore-failure"></a>Пропуск неудачи  
 Ошибка или усечение пропускается.  
  
### <a name="redirect-flow"></a>Перенаправление потока  
 Строка, вызывающая ошибку или усечение, направляется на вывод ошибок назначения ODBC. Дополнительные сведения см. в разделе, посвященном назначению ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Редактор назначения ODBC &#40;страница "Диспетчер соединений"&#41;](../../2014/integration-services/odbc-destination-editor-connection-manager-page.md)   
 [Редактор назначения ODBC (страница "Сопоставления")](../../2014/integration-services/odbc-destination-editor-mappings-page.md)  
  
  
