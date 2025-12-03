# Punto-6-estilo-de-codificaci-n-
Pequeño script simple para el punto 6 de la tarea 


        namespace Calcular_examen
        {
            public partial class Form1 : Form
            {
            public Form1()
            {
                InitializeComponent();
            }
            private void label1_Click(object sender, EventArgs e)
            {
    
            }
    
            private void Form1_Load(object sender, EventArgs e)
            {
    
            }
    
            private void label5_Click(object sender, EventArgs e)
            {
    
            }
            // --- Configuracion y valiacion de boton salir ---
    
            private void btnSalir_Click(object sender, EventArgs e)
            {
                if (MessageBox.Show("¿Desea salir?", "Cerrar", MessageBoxButtons.YesNo, MessageBoxIcon.Question, MessageBoxDefaultButton.Button3) == DialogResult.Yes)
                {
                    Application.Exit();
                }
            }
            // --- metodo limpiar controles ---
            public void Limpiar_Controles()
            {
                txtPErr.Text = "";
                txtPreAc.Text = "";
                txtPreNo.Text = "";
                txtTotalPre.Text = "";
                txtTotalPre.Focus();
            }
            // --- Boton limpiar controles ---
    
            private void btnBorrar_Click(object sender, EventArgs e)
            {
                Limpiar_Controles(); // Llamada del metodo limpiar
            }
    
            // --- validacion de solo aceptar numeros y no letras ---
    
            private void txtTotalPre_KeyPress(object sender, KeyPressEventArgs e)
            {
                if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar) && (e.KeyChar != '.'))
                {
                    e.Handled = true;
                    MessageBox.Show("Dato inválido, solo se aceptan numeros", "Error", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
                }
            }
    
            private void txtPreAc_KeyPress(object sender, KeyPressEventArgs e)
            {
                if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar) && (e.KeyChar != '.'))
                {
                    e.Handled = true;
                    MessageBox.Show("Dato inválido, solo se aceptan numeros", "Error", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
                }
            }
    
            private void txtPErr_KeyPress(object sender, KeyPressEventArgs e)
            {
                if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar) && (e.KeyChar != '.'))
                {
                    e.Handled = true;
                    MessageBox.Show("Dato inválido, solo se aceptan numeros", "Error", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
                }
            }
    
            private void txtPreNo_KeyPress(object sender, KeyPressEventArgs e)
            {
                if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar) && (e.KeyChar != '.'))
                {
                    e.Handled = true;
                    MessageBox.Show("Dato inválido, solo se aceptan numeros", "Error", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
                }
            }
    
            // --- Metodo suma ---
            public void suma()
            {
                int total_preguntas, preguntas_acertadas, preguntas_erroneas, preguntas_sin_responder, validar_preguntas, valor_Acertadas, valor_erroneas, valor0, total;
                total_preguntas = int.Parse(txtTotalPre.Text);
                preguntas_acertadas = int.Parse(txtPreAc.Text);
                preguntas_erroneas = int.Parse(txtPErr.Text);
                preguntas_sin_responder = int.Parse(txtPreNo.Text);
                validar_preguntas = preguntas_acertadas + preguntas_erroneas + preguntas_sin_responder;
                
                // --- validacion de total de preguntas ---
                if (total_preguntas < validar_preguntas || total_preguntas > validar_preguntas)
                {
                    MessageBox.Show("El numero de preguntas no corresponde a el total de ellas.", "Error", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
                }
                else 
                {
                    valor_Acertadas = preguntas_acertadas * 5;
                    valor_erroneas = preguntas_erroneas * -1;
                    valor0 = preguntas_sin_responder * 0;
                    total = valor_Acertadas + valor_erroneas + valor0;
    
                    MessageBox.Show($"La nota de su examen es: {total}.", "Nota", MessageBoxButtons.OK, MessageBoxIcon.Information, MessageBoxDefaultButton.Button1);
                }
    
            }
            // --- Boton calcular ---
    
            private void btncalcular_Click(object sender, EventArgs e)
            {
                // --- Validacion de espacios en blanco ---
                if (txtTotalPre.Text == "" | txtPreNo.Text == "" | txtPreAc.Text == "" | txtPErr.Text == "")
                {
                    MessageBox.Show("Por favor ingrese todos los parametros", "Precaución", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
                }
                else // --- Si los espacios no estan en blanco se realiza la operacion --- 
                {
                    suma(); // Llamado del metodo suma 
                }
            }
        }
    }
