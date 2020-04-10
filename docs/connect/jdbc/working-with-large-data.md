---
title: Работа с большими объемами данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c4a39cda0e2e0d0dc4bf2bee4254919829676a7a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923946"
---
# <a name="working-with-large-data"></a>Работа с большими объемами данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер JDBC реализует поддержку адаптивной буферизации, которая позволяет получать любые данные большого объема, не расходуя ресурсы на серверные курсоры. При адаптивной буферизации [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] получает результаты выполнения инструкций из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по мере того, как их запрашивает приложение, а не все сразу. Драйвер также удаляет результаты, когда приложение теряет к ним доступ.

В версии JDBC Driver 1.2 для [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] по умолчанию использовался режим **полной** буферизации. Если приложение не задавало свойству responseBuffering значение **adaptive** в свойствах подключения или с помощью метода [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) объекта [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), то драйвер поддерживал считывание с сервера всех результатов одновременно. Чтобы включить режим адаптивной буферизации, приложение должно было явно задать свойству подключения responseBuffering значение **adaptive**.  
  
Значение **adaptive** соответствует режиму буферизации по умолчанию, когда драйвер JDBC выполняет буферизацию для минимально необходимого объема данных. Дополнительные сведения об использовании адаптивной буферизации см. в [этой статье](../../connect/jdbc/using-adaptive-buffering.md).  
  
 Здесь представлены разделы, в которых описаны различные способы получения данных большого размера из базы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
| Раздел                                                                                                                      | Описание                                                              |
| -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [Пример считывания большого объема данных](../../connect/jdbc/reading-large-data-sample.md)                                               | Описывает получение данных большого объема с помощью инструкции SQL.       |
| [Пример считывания большого объема данных с помощью хранимых процедур](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md) | Описывает получение значений параметра CallableStatement OUT большого объема. |
| [Пример обновления большого объема данных](../../connect/jdbc/updating-large-data-sample.md)                                             | Описывает обновление данных большого объема в базе данных.                |
  
## <a name="see-also"></a>См. также раздел

[Примеры приложений JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)  
