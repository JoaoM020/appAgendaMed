import static jdk.javadoc.internal.doclets.formats.html.markup.HtmlStyle.title;

public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}

import 'package:flutter/material.dart';

void main() {
    runApp(AgendamedApp());
}

class AgendamedApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return MaterialApp(
                title: 'Agendamed',
                home: LoginScreen(),
                routes: {
            '/login': (_) => LoginScreen(),
                    '/register': (_) => RegisterScreen(),
                    '/recover1': (_) => RecoverStep1(),
                    '/recover2': (_) => RecoverStep2(),
                    '/home': (_) => HomeScreen(),
                    '/medication': (_) => MedicationScreen(),
                    '/delete': (_) => DeleteAccountScreen(),
        },
    );
    }
}

public class AgendamedAppImpl extends AgendamedApp { }


class LoginScreen extends StatelessWidget {
    final TextEditingController emailController = TextEditingController();
    final TextEditingController passwordController = TextEditingController();

    @override
    Widget build(BuildContext context) {
        return Scaffold(
                body: Padding(
                padding: EdgeInsets.all(16.0),
                child: Column(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
        Image.asset('assets/logo.png'),
                TextField(
                        controller: emailController,
                decoration: InputDecoration(labelText: 'Email'),
            ),
        TextField(
                controller: passwordController,
                obscureText: true,
                decoration: InputDecoration(labelText: 'Senha'),
            ),
        ElevatedButton(
                onPressed: () => Navigator.pushNamed(context, '/home'),
                child: Text('Entrar'),
            ),
        TextButton(
                onPressed: () => Navigator.pushNamed(context, '/register'),
                child: Text('Criar uma conta'),
            ),
        TextButton(
                onPressed: () => Navigator.pushNamed(context, '/recover1'),
                child: Text('Esqueci minha senha'),
            ),
          ],
        ),
      ),
    );
    }
}


class RegisterScreen extends StatelessWidget {
    final nameController = TextEditingController();
    final dobController = TextEditingController();
    final phoneController = TextEditingController();
    final emailController = TextEditingController();
    final passwordController = TextEditingController();

    @override
    Widget build(BuildContext context) {
        return Scaffold(
                appBar: AppBar(title: Text('Cadastro')),
        body: Padding(
                padding: EdgeInsets.all(16),
                child: Column(
                children: [
        TextField(decoration: InputDecoration(labelText: 'Nome'), controller: nameController),
        TextField(decoration: InputDecoration(labelText: 'Data de Nascimento'), controller: dobController),
        TextField(decoration: InputDecoration(labelText: 'Telefone'), controller: phoneController),
        TextField(decoration: InputDecoration(labelText: 'Email'), controller: emailController),
        TextField(decoration: InputDecoration(labelText: 'Senha'), controller: passwordController, obscureText: true),
        SizedBox(height: 16),
        ElevatedButton(onPressed: () {}, child: Text('Cadastrar')),
          ],
        ),
      ),
    );
    }
}


class RecoverStep1 extends StatelessWidget {
    final emailController = TextEditingController();
    final phoneController = TextEditingController();

    @override
    Widget build(BuildContext context) {
        return Scaffold(
                appBar: AppBar(title: Text('Recuperar senha')),
        body: Padding(
                padding: EdgeInsets.all(16),
                child: Column(
                children: [
        TextField(decoration: InputDecoration(labelText: 'Email'), controller: emailController),
        TextField(decoration: InputDecoration(labelText: 'Celular'), controller: phoneController),
        SizedBox(height: 16),
        ElevatedButton(
                onPressed: () => Navigator.pushNamed(context, '/recover2'),
                child: Text('Avançar'),
            ),
          ],
        ),
      ),
    );
    }
}


class RecoverStep2 extends StatelessWidget {
    final newPasswordController = TextEditingController();
    final confirmPasswordController = TextEditingController();

    @override
    Widget build(BuildContext context) {
        return Scaffold(
                appBar: AppBar(title: Text('Recuperar senha')),
        body: Padding(
                padding: EdgeInsets.all(16),
                child: Column(
                children: [
        TextField(decoration: InputDecoration(labelText: 'Nova senha'), controller: newPasswordController, obscureText: true),
        TextField(decoration: InputDecoration(labelText: 'Confirme sua nova senha'), controller: confirmPasswordController, obscureText: true),
        SizedBox(height: 16),
        ElevatedButton(onPressed: () {}, child: Text('Finalizar')),
          ],
        ),
      ),
    );
    }
}


class HomeScreen extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return Scaffold(
                appBar: AppBar(title: Text('Início')),
        drawer: Drawer(
                child: ListView(
                children: [
        DrawerHeader(child: Text('Menu')),
        ListTile(title: Text('Início'), onTap: () => Navigator.pushNamed(context, '/home')),
        ListTile(title: Text('Adicionar ou Editar Medicamento'), onTap: () => Navigator.pushNamed(context, '/medication')),
        ListTile(title: Text('Excluir conta'), onTap: () => Navigator.pushNamed(context, '/delete')),
          ],
        ),
      ),
        body: ListView(
                padding: EdgeInsets.all(16),
                children: [
        ListTile(title: Text('Amoxilina 20mg')),
        ListTile(title: Text('Paracetamol 750mg')),
        ListTile(title: Text('Dipirona 500mg')),
        ],
      ),
        floatingActionButton: FloatingActionButton(
                child: Icon(Icons.add),
                onPressed: () => Navigator.pushNamed(context, '/medication'),
      ),
    );
    }
}


class MedicationScreen extends StatelessWidget {
    final medController = TextEditingController();

    @override
    Widget build(BuildContext context) {
        return Scaffold(
                appBar: AppBar(title: Text('Medicação')),
        body: Padding(
                padding: EdgeInsets.all(16),
                child: Column(
                children: [
        TextField(
                controller: medController,
                decoration: InputDecoration(labelText: 'Nome da medicação e dosagem'),
            ),
        Row(
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: [
        ElevatedButton(onPressed: () {}, child: Text('Excluir')),
        ElevatedButton(onPressed: () {}, child: Text('Editar')),
              ],
            ),
          ],
        ),
      ),
    );
    }
}


class DeleteAccountScreen extends StatelessWidget {
    final emailController = TextEditingController();
    final passwordController = TextEditingController();
    bool accept = true;

    @override
    Widget build(BuildContext context) {
        return Scaffold(
                appBar: AppBar(title: Text('Apagar conta')),
        body: Padding(
                padding: EdgeInsets.all(16),
                child: Column(
                children: [
        TextField(decoration: InputDecoration(labelText: 'Email'), controller: emailController),
        TextField(decoration: InputDecoration(labelText: 'Senha'), controller: passwordController, obscureText: true),
        Row(
                children: [
        Checkbox(value: accept, onChanged: (val) {}),
        Text('Aceito apagar todos os meus dados'),
              ],
            ),
        ElevatedButton(onPressed: () {}, child: Text('Confirmar')),
          ],
        ),
      ),
    );
    }
}
