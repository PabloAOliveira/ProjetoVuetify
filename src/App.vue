<template>
  <v-app theme="dark">
    <v-navigation-drawer v-model="isDrawerOpen">
      <v-list>
        <v-list-subheader>Menu</v-list-subheader>
        <v-list-item prepend-icon="mdi-home"> Home </v-list-item>
        <v-list-item prepend-icon="mdi-account"> Usuários </v-list-item>

        <v-list-group value="Clientes">
          <template #activator="{ props }">
            <v-list-item v-bind="props" prepend-icon="mdi-account-circle"
              >Clientes</v-list-item
            >
          </template>

          <v-list-item prepend-icon="mdi-currency-usd">Faturamento</v-list-item>
          <v-list-item prepend-icon="mdi-chart-line">Relatório</v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar flat class="border-b">
      <v-app-bar-nav-icon
        @click="isDrawerOpen = isDrawerOpen = !isDrawerOpen"
      ></v-app-bar-nav-icon>
      <v-app-bar-title></v-app-bar-title>

      <template #append>
        <v-btn icon class="mr-1">
          <v-badge dot color="info">
            <v-icon icon="mdi-bell-outline"></v-icon>
          </v-badge>
        </v-btn>

        <v-menu>
          <template #activator="{ props }">
            <v-avatar v-bind="props">
              <v-img cover src="../src/img/portrait.png"></v-img>
            </v-avatar>
          </template>

          <v-card min-width="200px">
            <v-list :lines="false" density="compact" nav>
              <v-list-item prepend-icon="mdi-account-outline">
                <v-list-item-title>Meu Perfil</v-list-item-title>
              </v-list-item>

              <v-list-item prepend-icon="mdi-heart-outline">
                <v-list-item-title>Favoritos</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-menu>
      </template>
    </v-app-bar>
    <v-main>
      <v-container>

        <h1 class="mb-6">Dashboard</h1>

        <v-card flat class="border" mb-4>
          <div class="d-flex justify-space-between">
            <v-card-title>Últimos usuários</v-card-title>

            <v-card-title>
              <v-btn @click="isDialogOpen = true" variant="tonal" size="small"
                >Adicionar usuários</v-btn
              >

              <v-dialog v-model="isDialogOpen" width="600px">
                <v-card>
                  <v-card-title>Adicionar usuário</v-card-title>
                  <v-card-text>
                    <v-row>
                      <v-col>
                        <v-text-field label="Nome" variant="outlined"></v-text-field>
                      </v-col>
                      <v-col>
                        <v-text-field 
                        label="Email" 
                        variant="outlined"
                        :rules="emailRules"
                        ></v-text-field>
                      </v-col>
                    </v-row>

                    <v-select label="Cargo" variant="outlined" :items="['Admin','Gerente','Usuario']"></v-select>
                  </v-card-text>

                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn variant="text" @click="isDialogOpen = false">Cancelar</v-btn>
                    <v-btn variant="tonal" color="success" @click="isDialogOpen = false">Salvar</v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-card-title>
          </div>

          <v-table>
            <thead>
              <tr>
                <th>Nome</th>
                <th>Email</th>
                <th>Cargo</th>
                <th>Ações</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Fulano</td>
                <td>fulanoemail@gmail.com</td>
                <td><v-chip color="primary" variant="outlined" size="small">Admin</v-chip></td>
                <td>
                  <v-btn variant="tonal" color="primary">Editar</v-btn>
                </td>
              </tr>
              <tr>
                <td>Ciclano</td>
                <td>ciclanoemail@gmail.com</td>
                <td><v-chip color="success" variant="outlined" size="small">Gerente</v-chip></td>
                <td>
                  <v-btn variant="tonal" color="primary">Editar</v-btn>
                </td>
              </tr>
              <tr>
                <td>Beltrano</td>
                <td>beltranooemail@gmail.com</td>
                <td><v-chip variant="outlined" size="small">Usuario</v-chip></td>
                <td>
                  <v-btn variant="tonal" color="primary">Editar</v-btn>
                </td>
              </tr>
            </tbody>
          </v-table>
        </v-card>

        <v-row>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card flat class="border">
              <v-img class="align-end text-white" src="../src/img/img1.jpeg">
                <v-card-title>Top 10 Lugares</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3">Brasil RJ</v-card-subtitle>
              <v-card-text>
                <div>Rio De Janeiro</div>
                <div>Lorem Ipsum</div>
              </v-card-text>
              <v-card-actions>
                <v-btn variant="outlined" color="primary">Ver mais</v-btn>
                <v-btn prepend-icon="mdi-cart" variant="tonal" color="blue"
                  >Comprar</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card flat class="border">
              <v-img class="align-end text-white" src="../src/img/img1.jpeg">
                <v-card-title>Top 10 Lugares</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3">Brasil RJ</v-card-subtitle>
              <v-card-text>
                <div>Rio De Janeiro</div>
                <div>Lorem Ipsum</div>
              </v-card-text>
              <v-card-actions>
                <v-btn variant="outlined" color="primary">Ver mais</v-btn>
                <v-btn prepend-icon="mdi-cart" variant="tonal" color="blue"
                  >Comprar</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card flat class="border">
              <v-img class="align-end text-white" src="../src/img/img1.jpeg">
                <v-card-title>Top 10 Lugares no Mundo</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3">Brasil RJ</v-card-subtitle>
              <v-card-text>
                <div>Rio De Janeiro</div>
                <div>Lorem Ipsum</div>
              </v-card-text>
              <v-card-actions>
                <v-btn variant="outlined" color="primary">Ver mais</v-btn>
                <v-btn prepend-icon="mdi-cart" variant="tonal" color="blue"
                  >Comprar</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card flat class="border">
              <v-img class="align-end text-white" src="../src/img/img1.jpeg">
                <v-card-title>Top 10 Lugares no Mundo</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3">Brasil RJ</v-card-subtitle>
              <v-card-text>
                <div>Rio De Janeiro</div>
                <div>Lorem Ipsum</div>
              </v-card-text>
              <v-card-actions>
                <v-btn variant="outlined" color="primary">Ver mais</v-btn>
                <v-btn prepend-icon="mdi-cart" variant="tonal" color="blue"
                  >Comprar</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
      <HelloWorld />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },

  data: () => ({
    isDrawerOpen: false,
    isDialogOpen: false,
  }),
};
</script>
