<script>
import Keycloak from 'keycloak-js'

// Configuración de Keycloak
const keycloakConfig = {
    url: 'http://localhost:8080/', // Ejemplo: ''
    realm: 'dev-keycloak',
    clientId: 'keycloak-client-dev',
}

const keycloak = new Keycloak(keycloakConfig)

keycloak
    .init({ onLoad: 'login-required' })
    .then((auth) => {
        if (!auth) {
            console.log('Not Authenticated')
            window.location.reload()
        } else {
            console.log('Authenticated')
            new Vue({
                // tu configuración de Vue
            }).$mount('#app')
        }
    })
    .catch(() => {
        console.error('Authenticated Failed')
    })
</script>
<template>
    <main>
        <h1>hola</h1>
    </main>
</template>

<style scoped>
header {
    line-height: 1.5;
}

.logo {
    display: block;
    margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
    header {
        display: flex;
        place-items: center;
        padding-right: calc(var(--section-gap) / 2);
    }

    .logo {
        margin: 0 2rem 0 0;
    }

    header .wrapper {
        display: flex;
        place-items: flex-start;
        flex-wrap: wrap;
    }
}
</style>
