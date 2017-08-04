---
title: "Редактор источника «Excel» (страница «Диспетчер соединений») | Документы Microsoft"
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
- sql13.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c1f01be71a5093945a49c43a3a2aec334db7584b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="excel-source-editor-connection-manager-page"></a>Редактор источника Excel (страница «Диспетчер соединений»)
  Используйте раздел **Диспетчер соединений** диалогового окна **Редактор источника «Excel»** , чтобы выбрать используемую рабочую книгу [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] . Источник Excel считывает данные из рабочего листа или из именованного диапазона в существующей рабочей книге.  
  
> [!NOTE]  
>  Свойство **CommandTimeout** источника Excel недоступно в диалоговом окне **Редактор источника «Excel»**, но может быть задано с помощью диалогового окна **Расширенный редактор**. Дополнительные сведения о данном свойстве см. в подразделе «Источник Excel» раздела [Excel Custom Properties](../../integration-services/data-flow/excel-custom-properties.md).  
  
 Дополнительные сведения об источнике Excel см. в разделе [Excel Source](../../integration-services/data-flow/excel-source.md).  
  
## <a name="static-options"></a>Статические параметры  
 **диспетчер соединений OLE DB**  
 Выберите из списка существующий диспетчер подключений к Excel или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новый диспетчер подключений с помощью диалогового окна **Диспетчер подключений Excel** .  
  
 **Режим доступа к данным**  
 Укажите метод выбора данных из источника.  
  
|Значение|Description|  
|-----------|-----------------|  
|Таблица или представление|Получение данных из электронной таблицы или именованного диапазона файла Excel.|  
|Переменная, содержащая имя таблицы или представления|Укажите переменную, содержащую имя листа или диапазона.<br /><br /> **См. также:** [Использование переменных в пакетах](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|Команда SQL|Получение данных из файла Excel с использованием SQL-запроса. Дополнительные сведения о синтаксисе запросов см. в разделе [Excel Source](../../integration-services/data-flow/excel-source.md).|  
|Команда SQL из переменной|Задайте текст SQL-запроса в переменную.|  
  
 **Предварительный просмотр**  
 Осуществляйте предварительный просмотр результатов в диалоговом окне **Просмотр данных** . В окне «Предварительный просмотр» может отображаться до 200 строк.  
  
## <a name="data-access-mode-dynamic-options"></a>Динамические параметры режима доступа к данным  
  
### <a name="data-access-mode--table-or-view"></a>Режим доступа к данным = Таблица или представление  
 **Имя листа Excel**  
 Выберите в книге Excel из списка имя листа или именованного диапазона.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Режим доступа к данным — переменная, содержащая имя таблицы или представления  
 **Имя переменной**  
 Укажите переменную, содержащую имя листа или именованного диапазона.  
  
### <a name="data-access-mode--sql-command"></a>Режим доступа к данным — команда SQL  
 **Текст команды SQL**  
 Введите текст SQL-запроса, создайте запрос, нажав кнопку **Создать запрос**, или выберите файл, содержащий текст запроса, нажав кнопку **Обзор**.  
  
 **Параметры**  
 Если введен параметризованный запрос, где в тексте запроса в качестве заполнителя параметра использовался знак ?, воспользуйтесь диалоговым окном **Установка параметров запроса** для сопоставления входных параметров запроса и переменных пакета.  
  
 **Build query**  
 Воспользуйтесь диалоговым окном **Построитель запросов** для визуального конструирования SQL-запроса.  
  
 **Обзор**  
 Воспользуйтесь диалоговым окном **Открыть** для выбора файла, содержащего текст SQL-запроса.  
  
 **Анализ запроса**  
 Проверить синтаксис текста запроса.  
  
### <a name="data-access-mode--sql-command-from-variable"></a>Режим доступа к данным = Команда SQL из переменной  
 **Имя переменной**  
 Выберите переменную, содержащую текст SQL-запроса.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор источника «Excel» &#40; Страница «столбцы» &#41;](../../integration-services/data-flow/excel-source-editor-columns-page.md)   
 [Редактор источника «Excel» &#40; Страница «Вывод ошибок» &#41;](../../integration-services/data-flow/excel-source-editor-error-output-page.md)   
 [Диспетчер соединений с Excel](../../integration-services/connection-manager/excel-connection-manager.md)   
 [Цикл через Excel файлы и таблицы с помощью цикл](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  
