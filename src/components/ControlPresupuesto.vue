<script setup>
    import imagen from '../assets/img/grafico.jpg'
    import { formatearCantidad } from '../helpers'

    defineEmits(['reset-app'])

    const props = defineProps({
        presupuesto: {
            type: Number,
            required: true
        },
        disponible: {
            type: Number,
            required: true
        },
        gastado: {
            type: Number,
            required: true
        }
    })
</script>

<template>
    <div class="dos-columnas">
        <div class="contenedor-grafico">
            <img 
                :src="imagen"
            />
        </div>

        <div class="contenedor-presupesto">
            <button
                class="reset-app"
                type="button"
                @click="$emit('reset-app')"
            >Resetear App</button>
            
            <p>
                <span>Presupuesto:</span>
                {{ formatearCantidad( presupuesto )  }}
            </p>

            <p>
                <span>Disponible:</span>
                {{ formatearCantidad( disponible )  }}
            </p>

            <p>
                <span>Gastado:</span>
                {{ formatearCantidad( gastado )  }}
            </p>
        </div>
    </div>
</template>


<style scoped>
    .dos-columnas {
        display: flex;
        flex-direction: column;
    }

    .dos-columnas > :first-child {
        margin-bottom: 3rem;
    }

    @media (min-width: 768px) {
        .dos-columnas {
            flex-direction: row;
            gap: 4rem;
            align-items: center ;
        }
        .dos-columnas > :first-child {
        margin-bottom: 3rem;
        }
    }

    .reset-app{
        background-color: #DB2777;
        border: none;
        padding: 1rem;
        width: 100%;
        color: var(--blanco);
        font-weight: 900;
        text-transform: uppercase;
        border-radius: 1rem;
        transition-property: background-color;
        transition-duration: 300ms;
    }

    .reset-app:hover{
        cursor: pointer;
        background-color: #c11d67;
    }

    .contenedor-presupesto {
        width: 100%;
    }
    .contenedor-presupesto p {
        font-size: 2.4rem;
        text-align: center;
        color: var(--gris-oscuro);
    }
    @media (min-width: 768px) {
        .contenedor-presupesto p {
        text-align: left;
    }
    }
    .contenedor-presupesto span {
        font-weight: 900;
        color: var(--azul);
    }
</style>