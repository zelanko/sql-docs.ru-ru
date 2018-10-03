---
title: Включение ведения журнала для выполнения пакета на сервере служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 8930c63c-bc6f-46c2-b428-b3c29ee89a7d
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c6d1d614ee66731a24355a918678226dcc54ae35
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201654"
---
# <a name="enable-logging-for-package-execution-on-the-ssis-server"></a>Включение ведения журналов при выполнении пакета на сервере служб SSIS
  В этой процедуре описывается, как задать или изменить уровень ведения журнала для пакета, когда выполняется пакет, развернутый на сервере служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Уровень ведения журнала, задаваемый при выполнении пакета, переопределяет уровень, настроенный с помощью [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделе [Включение средств ведения журналов в SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md) .  
  
 Вы можете указать уровень ведения журнала с помощью одного из следующих методов. Этот раздел охватывает первый метод.  
  
-   Настройка экземпляра выполнения пакета с помощью диалогового окна «Выполнение пакета»  
  
-   Установка параметров для экземпляра выполнения с помощью [catalog.set_execution_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
  
-   Настройка задания агента SQL Server для выполнения пакета с помощью диалогового окна «Новый шаг задания».  
  
### <a name="to-set-the-logging-level-for-a-package-by-using-the-execute-package-dialog-box"></a>Задание уровня ведения журнала для пакета с помощью диалогового окна «Выполнение пакета»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]перейдите к пакету в обозревателе объектов.  
  
2.  Щелкните пакет правой кнопкой мыши и выберите команду **Выполнить**.  
  
3.  Выберите в диалоговом окне **Выполнение пакета** вкладку **Дополнительно** .  
  
4.  В разделе **Уровень ведения журнала**выберите уровень ведения журнала. В следующей таблице приведено описание возможных значений.  
  
5.  Настройте другие параметры пакета, а затем нажмите кнопку **ОК** , чтобы запустить пакет.  
  
 Доступны следующие уровни ведения журнала.  
  
|Уровень ведения журнала|Описание|  
|-------------------|-----------------|  
|None|Ведение журнала выключено. Регистрируется только состояние выполнения пакета.|  
|Basic|Записываются все события, за исключением пользовательских и диагностических событий. Это значение по умолчанию.|  
|Производительность|Регистрируются только статистика производительности, а также события OnError и OnWarning.<br /><br /> Отчет **Производительность выполнения** показывает активное и общее время компонентов потока данных пакета. Эта информация доступна, если уровень ведения журнала выполнения последнего пакета был задан как **Производительность** или **Подробно**. Дополнительные сведения см. в статье [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).<br /><br /> Представление [catalog.execution_component_phases](/sql/integration-services/system-views/catalog-execution-component-phases) отображает время начала и время окончания для компонентов потока данных для каждого этапа выполнения. Это представление содержит данные для этих компонентов, только если в качестве уровня ведения журнала выполнения пакета установлено значение **Производительность** или **Подробно**.|  
|Подробный|Регистрируются все события, в том числе пользовательские и диагностические события.<br /><br /> Пример диагностического события — DiagnosticEx. При каждом выполнении дочернего пакета задачей «Выполнение пакета» она заносит в журнал это событие. Сообщение о событии состоит из значений параметров, передаваемых дочерним пакетам.<br /><br /> Значением столбца сообщения для DiagnosticEx является XML-текст. . Для просмотра текста сообщения о выполнении пакета выполните запрос к представлению [catalog.operation_messages (база данных SSISDB)](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database).<br /><br /> Примечание: Пользовательские события относятся события, записываемые [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] задачи. Дополнительные сведения см. в разделе [Custom Messages for Logging](../../2014/integration-services/custom-messages-for-logging.md).<br /><br /> Представление [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) отображает строку каждый раз, когда компонент потока данных передает данные в компонент, находящийся ниже в иерархии, для выполнения пакета. Для сохранения этих данных в представлении уровень ведения журнала должен быть установлен в значение **Подробно** .|  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services &#40;SSIS&#41; ведение журнала](performance/integration-services-ssis-logging.md)   
 [Включение средств ведения журналов в SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)  
  
  
