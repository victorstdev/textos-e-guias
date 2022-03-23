# Protótipo Power BI SP
---
## Menu Carreira
### Colunas calculadas
- id_vazio = LOOKUPVALUE(Menu_Carreira[Employee ID], Efetivo[Employee ID], Menu_Carreira[Employee ID])
- Item = IF(
    Menu_Carreira[Atributo]="Work Experience - Last Updated", "Experiência Profissional",
    IF(Menu_Carreira[Atributo]="Career Interests - Last Updated", "Interesses na Carreira", 
    IF(Menu_Carreira[Atributo]="Job Interests - Last Updated", "Cargos de interesse",
    IF(Menu_Carreira[Atributo]="Relocation - Last Updated", "Realocação",
    IF(Menu_Carreira[Atributo]="Travel Preference - Last Updated", "Viagens",
    IF(Menu_Carreira[Atributo]="Education - Last Updated", "Formação",
    IF(Menu_Carreira[Atributo]="Job History - Last Updated", "Histórico de cargos",
    IF(Menu_Carreira[Atributo]="Languages - Last Updated", "Idiomas",
    IF(Menu_Carreira[Atributo]="Number of In-Progress Dev Items", "Itens em desenvolvimento",
    IF(Menu_Carreira[Atributo]="Number of Assessed Competencies for Worker", "Competências"))))))))))
### Medidas
- _qtd = CALCULATE(COUNT(Menu_Carreira[Sinal]), Menu_Carreira[Sinal] <> 0)
- _total = CALCULATE(COUNTROWS(Menu_Carreira), Menu_Carreira[id_vazio_carreira] <> BLANK())