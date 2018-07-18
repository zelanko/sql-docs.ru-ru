---
title: Настройка значений параметров после развертывания проекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eec0effad8cbdedabe3060609daf240a09fb88f3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291000"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a>Задать значения параметров после развертывания проекта
  Мастер развертывания позволяет задавать значения параметров по умолчанию сервера при развертывании проекта в каталог. После развертывания проекта в каталог задать значения по умолчанию сервера можно будет с помощью обозревателя объектов среды SQL Server Management Studio (SSMS) или Transact-SQL.  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a>Установка параметры по умолчанию сервера с помощью обозревателя объектов SSMS  
  
1.  Выберите и щелкните правой кнопкой мыши проект в узле **Службы Integration Services** .  
  
2.  Выберите пункт **Свойства** , чтобы открыть диалоговое окно **Свойства проекта** .  
  
3.  Откройте страницу «Параметры», нажав кнопку **Параметры** в разделе **Выбор страницы**.  
  
4.  Выберите нужный параметр в списке **Параметры** . Примечание. Столбец **Контейнер** помогает отличить параметры проекта от параметров пакета.  
  
5.  В столбце **Значение** укажите необходимое значение параметра по умолчанию сервера.  
  
 Чтобы установить параметры по умолчанию сервера с использованием Transact-SQL, используйте хранимую процедуру [catalog.set_object_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database). Для просмотра текущих значений по умолчанию сервера используйте запрос к представлению [catalog.object_parameters (база данных SSISDB)](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database). Чтобы удалить значение по умолчанию сервера, используйте хранимую процедуру, используйте хранимую процедуру [catalog.clear_object_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database).  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services &#40;SSIS&#41; параметров](integration-services-ssis-package-and-project-parameters.md)  
  
  
