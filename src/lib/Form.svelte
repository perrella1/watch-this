<script>
	import LoadingIndicator from './Loading.svelte';

	/**
	 * @type string
	 */
	export let cinemaType;
	/**
	 * @type Array<string>
	 */
	export let selectedCategories;
	/**
	 * @type string
	 */
	export let specificDescriptors;
	/**
	 * @type Boolean
	 */
	export let loading;

	const categoryTypes = [
		'Ação',
  'Aventura',
  'Animação',
  'Biografia',
  'Comédia',
  'Crime',
  'Documentário',
  'Drama',
  'Família',
  'Fantasia',
  'Filme Noir',
  'História',
  'Terror',
  'Musical',
  'Mistério',
  'Romance',
  'Ficção Científica',
  'Esporte',
  'Suspense',
  'Guerra',
  'Faroeste',
  'Cinema de Arte',
  'Comédia de Humor Negro',
  'Comédia Romântica',
  'Clássico Cult',
  'Comédia Sombria',
  'Épico',
  'Erótico',
  'Experimental',
  'Conto de Fadas',
  'Filme Dentro de um Filme',
  'Futurista',
  'Gângster',
  'Assalto',
  'Histórico',
  'Feriado/Festivo',
  'Independente',
  'Juvenil',
  'Melodrama',
  'Monstro',
  'Político',
  'Psicológico',
  'Filme de Estrada',
  'Sátira',
  'Ficção Científica',
  'Comédia Física (Slapstick)',
  'Questão Social',
  'Super-herói',
  'Surreal',
  'Adolescente',
  'Vampiro',
  'Zumbi'
	];

	let cinemaTypes = [
		{ value: 'tv show', title: 'Série/TV Show' },
		{ value: 'movie', title: 'Filme' },
		{ value: 'tv show or movie', title: 'Sem preferência' }
	];
</script>

<div class="pt-6 md:pt-10 text-slate-200">
	<div>
		<div class="mb-8">
			<div class="mb-4 font-semibold text-lg">Qual tipo está buscando?</div>
			<div class="flex items-center ">
				{#each cinemaTypes as type (type.value)}
					<button
						on:click={() => {
							cinemaType = type.value;
						}}
						class={`${
							cinemaType === type.value ? 'bg-pink-600/40 ' : ''
						} text-slate-200 font-bold mr-2 text-sm mt-2 py-2 px-4 rounded-full border border-pink-600 hover:bg-sky-600/20 cursor-pointer`}
					>
						{type.title}
					</button>
				{/each}
			</div>
		</div>
		<div>
			<div class="mb-4 font-semibold text-lg">
				Selecione as categorias de filmes ou séries que desejar.
			</div>
			<div class="flex items-center flex-wrap">
				{#each categoryTypes as category}
					<label
						class={`${
							selectedCategories.includes(category) ? 'bg-pink-600/40' : ''
						} text-slate-200 font-bold mr-2 mt-2 text-sm py-2 px-4 rounded-full border border-pink-600 hover:bg-sky-600/20 cursor-pointer`}
					>
						<input
							class="hidden"
							type="checkbox"
							bind:group={selectedCategories}
							name="categories"
							value={category}
						/>
						{category}
					</label>
				{/each}
			</div>
		</div>
		<div class="mt-8">
			<div class="mb-4 font-semibold text-lg">
				Fique a vontade de escrever qualquer detalhe ou preferência que
				desejar. Quanto mais específico, melhor!
			</div>
			<textarea
				bind:value={specificDescriptors}
				class="bg-white/40 border border-white/0 p-2 rounded-md placeholder:text-slate-800 text-slate-900 w-full h-20 font-medium"
				placeholder="Ex. Ter ao menos 2 temporadas e estar na Netflix. Ou ser um filme de ação com o Tom Cruise."
			/>
			<button
				on:click
				class={`${
					loading
						? 'bg-pink-400/50'
						: 'bg-pink-600 hover:bg-gradient-to-r from-pink-700 via-pink-600 to-pink-700 '
				} mt-4 w-full h-10 text-white font-bold p-3 rounded-full flex items-center justify-center`}
			>
				{#if loading}
					<LoadingIndicator />
				{:else}
					<p>Buscar Filmes</p>
				{/if}
			</button>
		</div>
	</div>
</div>
