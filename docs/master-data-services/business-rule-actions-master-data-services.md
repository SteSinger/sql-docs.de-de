---
title: Geschäftsregelaktionen
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cdc4daca-3dff-46d8-b7f0-57f7826dd61a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3aa704289844143dc07f63a384269a1ff45f31b9
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729735"
---
# <a name="business-rule-actions-master-data-services"></a>Geschäftsregelaktionen (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]sind Geschäftsregelaktionen die Folge von Geschäftsregel-Bedingungsauswertungen. Wenn eine Bedingung erfüllt ist (TRUE), wird die Aktion initiiert.  
  
> [!NOTE]  
>  Für Standardwert- und Wertänderungsaktionen wird der generierte Wert abgeschnitten, falls er die maximale Attributlänge überschreitet.  
  
## <a name="default-value-actions"></a>Standardwertaktionen  
 Über**Standardwert** -Aktionen wird der Standardwert eines bestimmten Attributs festgelegt. Benutzer mit entsprechender Berechtigung können diese Standardwerte ändern.  
  
|Wertname|und Beschreibung|  
|----------------|-----------------|  
|**Entspricht standardmäßig**|Das ausgewählte Attribut **entspricht standardmäßig** einem bestimmten Attribut oder Attributwert bzw. ist leer.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**Entspricht standardmäßig einem generierten Wert**|Das ausgewählte Attribut **entspricht standardmäßig einem generierten Wert** , der durch Eingabe eines Startwerts und eines inkrementellen Werts bestimmt wird.<br /><br /> Diese Aktion ist für Text- und Nummernwerte gültig.|  
|**Entspricht standardmäßig einem verketteten Wert**|Das ausgewählte Attribut **entspricht standardmäßig einem verketteten Wert** , der durch Angabe mehrerer Attribute bestimmt wird.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
  
## <a name="change-value-actions"></a>Wertänderungsaktionen  
 Durch Aktionen vom Typ**Wert ändern** wird der Wert eines angegebenen Attributs oder Attributwerts geändert. Benutzer können diese Werte nur ändern, wenn der neue Wert bewirkt, dass die Aktion TRUE ergibt.  
  
|Wertname|und Beschreibung|  
|----------------|-----------------|  
|**Ist gleich**|Das ausgewählte Attribut wird in einen definierten Attributwert oder ein anderes Attribut geändert bzw. ist leer.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**Entspricht einem verketteten Wert**|Das ausgewählte Attribut wird in einen verketteten Wert geändert, der durch Angabe mehrerer Attribute bestimmt wird.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
  
## <a name="validation-actions"></a>Überprüfungsaktionen  
 Wenn zur**Überprüfung** ausgeführte Aktionen nicht TRUE ergeben, wird eine E-Mail an einen bestimmten Benutzer oder eine bestimmte Gruppe gesendet. Um für eine Version einen Commit auszuführen, müssen alle Überprüfungsaktionen TRUE ergeben.  
  
 Die einzigen Ausnahmen sind die Aktionen **ist verbindlich** und **ist ungültig** . Diese Aktionen müssen mit einer Aktion zum Ändern von Werten kombiniert werden, damit die Daten erfolgreich überprüft werden können und ein Commit für die Version ausgeführt werden kann.  
  
|Name der Überprüfung|und Beschreibung|  
|---------------------|-----------------|  
|**Ist erforderlich**|Das ausgewählte Attribut **ist erforderlich**, es kann also nicht NULL lauten oder leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**ist ungültig**|Das ausgewählte Attribut **ist ungültig**.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**Muss das Muster enthalten**|Das ausgewählte Attribut **muss das Muster enthalten** , das angegeben ist. Verwenden Sie reguläre Ausdrücke von .NET Framework, um das Muster anzugeben.<br /><br /> Weitere Informationen zu regulären Ausdrücken finden Sie unter [Sprachelemente für reguläre Ausdrücke](https://go.microsoft.com/fwlink/?LinkId=164401) in der MSDN Library.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
|**Muss eindeutig sein**|Das ausgewählte Attribut **muss eindeutig sein** , und zwar unabhängig von definierten Attributen oder in Kombination mit ihnen.<br /><br /> **Bewährte Methode** : Kombinieren Sie diese Aktion mit einer verbindlichen Bedingung, um sicherzustellen, dass Indexfelder in Abonnementsystemen gültig sind.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.<br /><br /> **HINWEIS**: Wenn das erste Attribut vom Typ „DateTime“ ist, kann es nicht in Kombination mit einem Attribut vom Typ „Numeric“ oder „Text“ verwendet werden. Wenn das erste Attribut vom Typ „Numerisch“ ist, kann es nicht in Kombination mit einem Attribut vom Typ „DateTime“ verwendet werden.|  
|**Muss einen der folgenden Werte aufweisen**|Das ausgewählte Attribut **muss einen der folgenden Werte aufweisen** , die in einer Liste angegeben sind.<br /><br /> Diese Aktion ist für Textwerte gültig.|  
|**Muss größer sein als**|Das ausgewählte Attribut **muss größer sein als** ein bestimmtes Attribut oder ein bestimmter Attributwert bzw. muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**Muss gleich sein**|Das ausgewählte Attribut **muss gleich sein** , und zwar mit einem definierten Attributwert oder einem anderen Attribut bzw. es muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**Muss größer als oder gleich sein**|Das ausgewählte Attribut **muss größer als oder gleich sein** , und zwar mit einem bestimmten Attribut oder Attributwert bzw. es muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**Muss kleiner sein als**|Das ausgewählte Attribut **muss kleiner sein als** ein bestimmtes Attribut oder ein bestimmter Attributwert bzw. es muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**Muss kleiner als oder gleich sein**|Das ausgewählte Attribut **muss kleiner als oder gleich sein** , und zwar mit einem bestimmten Attribut oder Attributwert bzw. es muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**Muss liegen zwischen**|Das ausgewählte Attribut **muss liegen zwischen** zwei bestimmten Attributen oder Attributwerten.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**Muss eine Mindestlänge haben von**|Das ausgewählte Attribut **muss eine Mindestlänge haben vom** angegebenen Wert.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
|**Muss eine Höchstlänge haben von**|Das ausgewählte Attribut **muss eine Höchstlänge haben vom** angegebenen Wert.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
  
## <a name="external-action"></a>Externe Aktion  
 **Externe** Aktionen interagieren mit Anwendungen außerhalb von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
|Aktionsname|und Beschreibung|  
|-----------------|-----------------|  
|**start workflow**|Initiiert einen externen Workflow. Die Daten, die diese Aktion bewirkt haben, werden an den Workflow übergeben. Weitere Informationen finden Sie unter [SharePoint Workflow Integration with Master Data Services](https://msdn.microsoft.com/library/gg690195.aspx).<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
  
## <a name="see-also"></a>Siehe auch  
 [Geschäftsregelbedingungen &#40;Master Data Services&#41;](../master-data-services/business-rule-conditions-master-data-services.md)   
 [Geschäftsregeln &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)   
 [Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)  
  
  
