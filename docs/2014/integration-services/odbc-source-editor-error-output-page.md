---
title: Редактор источника «ODBC» (страница «вывод ошибок») | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.errorhandling.f1
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b19a94e71eaef45184c1777ce299809b2b2d7f8d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66057132"
---
# <a name="odbc-source-editor-error-output-page"></a>Редактор источника «ODBC» (страница «Вывод ошибок»)
  Страница **Вывод ошибок** диалогового окна **Редактор источника ODBC** используется для выбора параметров обработки ошибок.  
  
 Дополнительные сведения об источнике ODBC см. в разделе [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>список задач  
 **Открытие страницы «Вывод ошибок» редактора источника ODBC**  
  
-   В среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]откройте пакет служб [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] , содержащий источник ODBC.  
  
-   На вкладке **Поток данных** дважды щелкните источник ODBC.  
  
-   В окне **Редактор источника ODBC**нажмите кнопку **Вывод ошибок**.  
  
## <a name="options"></a>Параметры  
  
### <a name="inputoutput"></a>Ввод-вывод  
 Просмотр имени источника данных.  
  
### <a name="column"></a>Столбец  
 Не используется.  
  
### <a name="error"></a>Ошибка  
 Выберите порядок обработки ошибок в потоке источником ODBC: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
### <a name="truncation"></a>Усечение  
 Выберите порядок обработки усечений в потоке источником ODBC: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
### <a name="description"></a>Описание  
 Не используется.  
  
### <a name="set-this-value-to-selected-cells"></a>Присвоить указанное значение выбранным ячейкам  
 Выберите, как источник ODBC обрабатывает все выбранные ячейки при возникновении ошибки или усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
### <a name="apply"></a>Применить  
 Примените параметры обработки ошибок к выбранным ячейкам.  
  
## <a name="error-handling-options"></a>Параметры обработки ошибок  
 Следующие параметры позволяют настроить обработку ошибок и усечений источником ODBC.  
  
### <a name="fail-component"></a>Компонент, завершившийся сбоем  
 Задача потока данных заканчивается сбоем, если возникли ошибка или усечение. Это поведение по умолчанию.  
  
### <a name="ignore-failure"></a>Пропуск неудачи  
 Ошибка или усечение пропускается.  
  
### <a name="redirect-flow"></a>Перенаправление потока  
 Строка, вызывающая ошибку или усечение, направляется на вывод ошибок источника ODBC. Дополнительные сведения см. в статье [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="see-also"></a>См. также  
 [Редактор источника ODBC &#40;страница "Диспетчер соединений"&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md)   
 [Редактор источника ODBC (страница "Столбцы")](../../2014/integration-services/odbc-source-editor-columns-page.md)  
  
  
