---
description: Сопоставления параметров запросов с переменными в компонентах потока данных
title: Сопоставления параметров запросов с переменными в компонентах потока данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d9cb92a6815e41bfffbcf449c98077ab71d25467
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430826"
---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a>Сопоставления параметров запросов с переменными в компонентах потока данных

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  При настройке конфигурации источника OLE DB для использования параметризованных запросов можно сопоставить параметры с переменными.  
  
 В источнике OLE DB параметризованные запросы используются для фильтрации данных при подключении источника к источнику данных.  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>Сопоставление параметра запроса с переменной  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Щелкните вкладку **Поток данных** и перетащите источник OLE DB из **области элементов**в область конструктора.  
  
4.  Щелкните правой кнопкой источник OLE DB и выберите пункт **Правка**.  
  
5.  В окне **Редактор источника OLE DB**выберите диспетчер соединений OLE DB, предназначенный для подключения к источнику данных, или нажмите кнопку **Создать** , чтобы создать новый диспетчер соединений OLE DB.  
  
6.  Выберите параметр **Команда SQL** для режима доступа к данным, а затем введите параметризированный запрос панели **Текст команды SQL** .  
  
7.  Нажмите **Параметры**.  
  
8.  В диалоговом окне **Установка параметров запроса** сопоставьте каждый параметр в списке **Параметры** с переменной в списке **Переменные** или создайте переменную, щелкнув **\<New variable>** . Нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  Для сопоставления доступны только системные и пользовательские переменные, находящиеся в области видимости данного пакета, родительского контейнера, такого как «цикл по каждому элементу», или задачи потока данных, содержащей компоненты потока данных, доступные для сопоставления. Переменная должна иметь тип данных, совместимый со столбцом в предложении WHERE, которому назначен параметр.  
  
9. Чтобы просмотреть до 200 строк данных, возвращаемых запросом, нажмите кнопку **Предварительный просмотр** .  
  
10. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [Источник OLE DB](../../integration-services/data-flow/ole-db-source.md)   
 [Преобразование "Уточняющий запрос"](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
