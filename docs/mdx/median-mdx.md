---
title: Valeur médiane (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e962507d6e437974708aa042919ea6fb7bd632d0
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741678"
---
# <a name="median-mdx"></a>Median (MDX)


  Retourne la valeur médiane d'une expression numérique évaluée sur un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Median(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, cette expression est évaluée sur le jeu, puis retourne la valeur médiane produite par cette évaluation. Si aucune expression numérique n'est précisée, le jeu spécifié est évalué dans le contexte actuel des membres du jeu, puis retourne la valeur médiane de l'évaluation.  
  
 La valeur médiane est la valeur de milieu d'un jeu de nombres ordonnés. (La valeur médiane n'est pas la moyenne, qui est la somme d'un ensemble de chiffres divisée par le nombre de chiffres présents dans cet ensemble). La valeur médiane est déterminée en choisissant la plus petite valeur de sorte que la moitié au moins des valeurs du jeu ne soient pas supérieures à la valeur choisie. Si le nombre des valeurs du jeu est impair, la valeur médiane correspond à une seule valeur. Si le nombre des valeurs du jeu est pair, la valeur médiane correspond à la somme des deux valeurs du milieu divisée par deux.  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignore les valeurs NULL lors du calcul de la valeur médiane dans un jeu de nombres ordonnés.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne les ventes mensuelles médianes de chaque trimestre, sous-catégorie et chaque pays inscrit dans le cube Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Median   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
