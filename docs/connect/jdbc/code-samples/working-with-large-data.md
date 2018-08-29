---
title: Работа с большими объемами данных | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 728e86f155a1bb61c7fe900f5e536eed991c206a
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785544"
---
# <a name="working-with-large-data"></a>Работа с большими объемами данных

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Драйвер JDBC реализует поддержку адаптивной буферизации, которая позволяет получать любые данные большого объема, не расходуя ресурсы на серверные курсоры. При адаптивной буферизации [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] получает результаты выполнения инструкций из экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по мере того, как их запрашивает приложение, а не все сразу. Драйвер также удаляет результаты, когда приложение теряет к ним доступ.  
  
В версии JDBC Driver 1.2 для [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] по умолчанию использовался режим **полной** буферизации. Если приложение не задавало свойству responseBuffering значение **adaptive** в свойствах подключения или с помощью метода [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), то драйвер поддерживал считывание с сервера всех результатов одновременно. Чтобы включить режим адаптивной буферизации, приложение должно было явно задать свойству подключения responseBuffering значение **adaptive**.  
  
Значение **adaptive** соответствует режиму буферизации по умолчанию, когда драйвер JDBC выполняет буферизацию для минимально необходимого объема данных. Дополнительные сведения об использовании адаптивной буферизации см. в разделе [Using Adaptive Buffering](../../../connect/jdbc/using-adaptive-buffering.md).  
  
Здесь представлены разделы, в которых описаны различные способы получения данных большого размера из базы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
| Раздел                                                                                                                         | Описание                                                              |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [Пример считывания данных большого объема](../../../connect/jdbc/code-samples/reading-large-data-sample.md)                                               | Описывает получение данных большого объема с помощью инструкции SQL.       |
| [Пример считывания данных большого объема с помощью хранимых процедур](../../../connect/jdbc/code-samples/reading-large-data-with-stored-procedures-sample.md) | Описывает получение значений параметра CallableStatement OUT большого объема. |
| [Пример обновления данных большого объема](../../../connect/jdbc/code-samples/updating-large-data-sample.md)                                             | Описывает обновление данных большого объема в базе данных.                |
  
## <a name="see-also"></a>См. также:

[Пример приложений драйвера JDBC](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
  