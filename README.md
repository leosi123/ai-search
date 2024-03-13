# ai-search
Resposta ao desafio DIO AI search
## Passo a passo para configurar AI search
<li>1-Criar o Azure AI Search resource no portal azure, escolhendo o plano de preço desejado, como é só o laboratorio escolheremos o o basico</li>
<li>2-Criar o Azure AI services resource. Ele deve ser no mesmo local do resource anterior. Escolha o plano de preço mais interessante e crie o recurso</li>
<li>3-Criar storage account. Depois de criado ir em settings, configaration e habilite o acesso anonimo ao blob</li>
<li>4-Dentro do storage account, clicar no menu esquerdo em containers.</li>
<li>5-Crie um novo container com o nome coffee-reviews. Em nivel de acesso publico selecione container.</li>
<li>6-Baixe os arquivos de reviews do link https://aka.ms/mslearn-coffee-reviews e extraia na pasta reviews localmente</li>
<li>7-Agora no azure portals, na sua storage accouint clicque no seu container novo e faça o upload de todas as reviews extraídas na pasta review do ceu computador.</li>
<li>8-No azure ai search, clique em overview e depois em importar dados.</li>
<li>9-Escolha como data source azure blob storage, em seguida preencha os seguintes parâmetros:
<li>ata Source: Azure Blob Storage</li>
<li>Data source name: coffee-customer-data</li>
<li>Data to extract: Content and metadata</li>
<li>Parsing mode: Default</li>
<li>Connection string: *Select Choose an existing connection. Select your storage account, select the coffee-reviews container, and then click Select.</li>
<li>Managed identity authentication: None</li>
<li>Container name: this setting is auto-populated after you choose an existing connection.</li>
<li>Blob folder: Leave this blank.</li>
<li>Description: Reviews for Fourth Coffee shops.  </li>
</li>
<li>10-Clique em next</li>
<li>11-Na seção Attach Cognitive Services; Selecione seu azure ai services resource</li>
<li>12-na seção Add enrichments: Selecione os seguintes parâmetros:
  <li>Skillset name:coffee-skillset</li>
  <li>Selecione a checkbox Enable OCR and merge all text into merged_content field</li>
  <li>Enrichment granularity level:Pages (5000 character chunks)</li>
  <li>Não selecione: Enable incremental enrichment</li>
  <li>Selecione os seguintes campos enriquecidos:
<li>Extract location names	 	locations</li>
<li>Extract key phrases	 	keyphrases</li>
<li>Detect sentiment	 	sentiment</li>
<li>Generate tags from images	 	imageTags</li>
<li>Generate captions from images	 	imageCaption</li>
</li>
</li>
<li>13-Em Save enrichments to a knowledge store. Selecione:
<li>Image projections</li>
<li>Documents</li>
<li>Pages</li>
<li>Key phrases</li>
<li>Entities</li>
<li>Image details</li>
<li>Image references</li>
</li>
<li>14-Em Azure blob projections selecione Document</li>
<li>15-Clique em next</li>
<li>16-Mude Index name para coffee-index.</li>
<li>17-Selecione filterable para todos os campos pre-selecionados</li>
<li>18-Clique em next</li>
<li>19-Troque o Indexer name para coffee-indexer, schedule = ONce</li>
<li>20-Clique em submit e espere o indexer ser criado.</li>
<li>21-Na aba overview do search service, clique em search explorer</li>
<li>22-Troque a view para JSON</li>
<li>23-Teste a procura com os seguintes JSON</li>
<li>{
    "search": "*",
    "count": true
}</li>
<li>{
 "search": "locations:'Chicago'",
 "count": true
}</li>
<li>{
 "search": "sentiment:'negative'",
 "count": true
}</li>
<li>Veja como é possível procurar os documentos e ver seus atributos.</li>
<li></li>


