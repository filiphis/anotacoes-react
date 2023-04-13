# Rotas no React com React Router DOM

Instalando o React Router Dom
	yarn add react-router-dom



componentes do React Router DOM
	
	<BrowserRouter>
		<Routes>
			<Route path="/" element={<Home />}
				Tem o mesmo funcionamento do link html, porem transforma o site em "SPA"
			
		<Routes/>
	</ BrowserRouter>
	


Criando um layout padrão que irá ser utilizado por varias rotas
Exemplo:

export function DefaultLayout() {
	return(
		<Header />
		<Outlet /> -- É um componente do RouterDom utilaizado como um "espaço" para substituir conteudos  
		<Footer />
	)
}


	<BrowserRouter>
		<Routes>
			<Route path="/" element={DefaultLayout}> -- path="/" informa que o layout DefaultLayout será aplicado a todas as rotas filhas da rota /
				<Route path="/" element={<Home />} -- Tem o mesmo funcionamento do link html, porem transforma o site em "SPA"
			</ Route>
		<Routes/>
	</ BrowserRouter>



















