---
title: "Предварительный просмотр данных диалоговое окно «» (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.previewdata.f1
ms.assetid: 423ac26a-ba02-4fdf-88b4-07995fe4a97e
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bfa75d2c1d2d50d1f0205fed22811ddbb3b96747
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="preview-data-dialog-box-sql-server-import-and-export-wizard"></a>Диалоговое окно «Просмотр данных» (мастер импорта и экспорта SQL Server)
  После указания данных, которые необходимо скопировать, можно нажать кнопку **Просмотр** , чтобы открыть диалоговое окно **Просмотр данных** . На этой странице можно просмотреть до 200 строк образца данных из источника данных. Таким образом вы убедитесь, что мастер будет копировать именно необходимые данные.
  
## <a name="screen-shot-of-the-preview-data-page"></a>Снимок экрана: страница "Просмотр данных" 
 На следующем снимке экрана показано диалоговое окно **Просмотр данных** мастера.  
 
![Предварительный просмотр страницы данных из мастера импорта и экспорта](../../integration-services/import-export-data/media/preview-data.png "страницу Предварительный просмотр данных мастер импорта и экспорта")  
  
## <a name="preview-sample-data"></a>Просмотр образца данных  
 **Источник**  
Отображает запрос, используемый мастером для загрузки данных из источника данных.

Если выбрана таблица, чтобы скопировать, **источника** поле показывает `SELECT * FROM <table>` запроса вместо имени таблицы. 
  
 **Сетка образца данных**  
 Отображает до 200 строк образца данных, возвращаемых запросом из источника данных.  


## <a name="thats-not-right-i-want-to-change-something"></a>Это не так, что-то изменить
После просмотра данных может потребоваться изменить параметры, выбранные на предыдущих страницах мастера. Для внесения этих изменений, нажмите кнопку **ОК** для возврата **Выбор исходных таблиц и представлений** и нажмите кнопку **обратно** для возврата на предыдущие страницы, где можно изменить на Выбранные параметры.

## <a name="whats-next"></a>Дальнейшие действия  
 После просмотра данных, которые требуется скопировать, и нажатия кнопки **ОК**диалоговое окно **Просмотр данных** вернет вас на страницу **Выбор исходных таблиц и представлений** или на страницу **Настройка назначения "Неструктурированный файл"** . Дополнительные сведения см. в разделах [Выбор исходных таблиц и представлений](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) или [Настройка назначения "Неструктурированный файл"](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>См. также:
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)

