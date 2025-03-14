# Automatización de Contratos

La clase `ContractExtractor` permite extraer caracteristicas de contratos en PDF.

## Quickstart

1. Crear entorno virtual e instalar dependencias
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

2. Popular el folder **contratos** con los PDFs de contratos a procesar

3. Ejecutar el notebook **'src_notebook.ipynb'**.

El excel con todos los campos extraidos se encontrara en el archivo **'/output/output.xlsx'**.

## Documentacion Técnica

### Funcionamiento
1. En primer lugar, cada documento es validado. Se verifica que se encuentra en el formato correcto (PDF) y que tiene mas de 200 caracteres. El resultado del proceso de validacion se muestra con las columnas:
- **valid**: Un booleano que refleja la validez del documento PDF.
- **valid_note**: Notas que explican el error de validez.

2. Luego, se extrae programaticamente cada campo, junto a otras 4 columnas que describen su extraccion:
- **[Campo]**: El valor extraido
- **[Campo] Found**: Un booleano que representa si el valor fue encontrado en el documento
- **[Campo] Origin**: Una cadena de texto que lista todos los parrafos que fueron utilizados para extraer el campo (Contexto).
- **[Campo] Confidence**: El nivel de confianza en la certeza de la extraccion. Puede ser 'low', 'medium' y 'high'.
- **[Campo] Notes**: Notas que explican el proceso de extraccion.

### Paralelismo

Se implementó la funcion `parallel_apply` para permitir procesar multiples contratos al mismo tiempo y reducir significativamente el tiempo de carga.