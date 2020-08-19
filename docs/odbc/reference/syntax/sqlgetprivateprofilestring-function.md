---
description: Функция SQLGetPrivateProfileString
title: Функция SQLGetPrivateProfileString | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetPrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetPrivateProfileString
helpviewer_keywords:
- SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2223d46d507df2a9cf82e7feb800caf5b8f82cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421238"
---
# <a name="sqlgetprivateprofilestring-function"></a>Функция SQLGetPrivateProfileString
**Соответствия**  
 Введенная версия: ODBC 2,0  
  
 **Сводка**  
 **SQLGetPrivateProfileString** возвращает список имен значений или данных, соответствующих значению системной информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
int SQLGetPrivateProfileString(  
     LPCSTR   lpszSection,  
     LPCSTR   lpszEntry,  
     LPCSTR   lpszDefault,  
     LPCSTR   RetBuffer,  
     INT      cbRetBuffer,  
     LPCSTR   lpszFilename);  
```  
  
## <a name="arguments"></a>Аргументы  
 *лпсзсектион*  
 Входной Указывает на строку, завершающуюся нулем, которая указывает раздел, содержащий имя ключа. Если этот аргумент имеет значение NULL, функция копирует все имена разделов в файле в указанный буфер.  
  
 *лпсзентри*  
 Входной Указывает на строку, завершающуюся нулем, содержащую имя ключа, связанную строку которой необходимо получить. Если этот аргумент имеет значение NULL, все имена ключей в разделе, указанном аргументом *лпсзсектион* , копируются в буфер, указанный аргументом *ретбуффер* .  
  
 *лпсздефаулт*  
 Входной Указывает на строку, завершающуюся нулем, которая указывает значение по умолчанию для данного ключа, если ключ не найден в файле инициализации. Этот аргумент не может иметь значение NULL.  
  
 *ретбуффер*  
 Проверки Указывает на буфер, который получает извлеченную строку.  
  
 *кбретбуффер*  
 Входной Задает размер (в символах) буфера, на который указывает аргумент *ретбуффер* .  
  
 *лпсзфиленаме*  
 Входной Указывает на строку, завершающуюся нулем, которая присваивает имя файлу инициализации. Если этот аргумент не содержит полный путь к файлу, поиск выполняется по каталогу по умолчанию.  
  
## <a name="returns"></a>Возвращаемое значение  
 **SQLGetPrivateProfileString** возвращает целочисленное значение, указывающее количество считанных символов.  
  
## <a name="diagnostics"></a>Диагностика  
 При сбое вызова **SQLGetPrivateProfileString** можно получить связанное значение * \* Пферроркоде* , вызвав **склинсталлереррор**. В следующей таблице перечислены значения * \* пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установщика|Произошла ошибка, для которой не возникала конкретная ошибка установщика.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщику не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLGetPrivateProfileString** предоставляется как простой способ переноса драйверов и библиотек DLL установки драйверов из Microsoft® Windows® в Microsoft Windows NT®/Виндовс 2000. Вызовы **жетприватепрофилестринг** , которые извлекают строку профиля из файла Odbc.ini, должны быть заменены вызовами **SQLGetPrivateProfileString**. **SQLGetPrivateProfileString** вызывает функции в API Win32® для получения запрашиваемых имен значений или данных, соответствующих значению подраздела Odbc.ini сведений о системе.  
  
 Режим конфигурации (заданный параметром **склсетконфигмоде**) указывает, где в сведениях о системе отображается запись Odbc.ini, в которой ПЕРЕЧИСЛЕНЫ значения DSN. Если DSN является пользовательским именем пользователя (режим конфигурации — USERDSN_ONLY), функция считывает из записи Odbc.ini в HKEY_CURRENT_USER. Если DSN является системным именем DSN (SYSTEMDSN_ONLY), функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если используется режим конфигурации БОСДСН, то HKEY_CURRENT_USER пытается выполнить операцию, а в случае неудачи — HKEY_LOCAL_MACHINE.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Запись значения в сведения о системе|[склвритеприватепрофилестринг](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
