# Maç Bilet Satışı
Maç Bileti Satış Uygulaması

Yapacağım uygulama spor dallarında maçı izlemek için bilet alım satışı yapmak için bir uygulama oluşturmak.

UYGULAMANIN İÇERİĞİ

Uygulamada bir taraftar veya seyirci gideceği maçı alacağı bileti gideceği tarih ve saati seçerek izlemek istediği gösteriyi-maçları listeleyip arasından seçim yapacaktır.

UYGULAMANIN YAPIM YERİ

Uygulama Windows Forms ile yapılacak.

UYGULAMA NASIL İŞLİYOR

Yukarıdaki örnekte, BiletSatisFormukoleksiyonlarda bulunan bir Windows Forms formülü oluşturuldu. Formda, 
kullanıcıların adına, e-posta adresi, takım seçimini, stad seçimini ve bilet tüketmesi için gerekli kontroller bulunuyor.
Kullanıcı "Satın Al" düğmesine tıkladığında, gerekli bilgileri alacak ve ardından satın almayı gerçekleştirecektir.


Kod Görseli Bu Şekilde


{

 using System; 
 using System.Windows.Forms;
 namespace MacBiletSatisUygulamasi
  
      public partial class BiletSatisFormu : Form
    {
        // Örnek veriler için bir liste
        private string[] takimlar = { "Takım A", "Takım B", "Takım C" };
        private string[] stadlar = { "Stad 1", "Stad 2", "Stad 3" };

        public BiletSatisFormu()
        {
            InitializeComponent();

            // Form yüklenirken verileri doldur
            cmbTakimlar.DataSource = takimlar;
            cmbStadlar.DataSource = stadlar;
        }

        private void btnSatinal_Click(object sender, EventArgs e)
        {
            // Kullanıcı bilgilerini al
            string adSoyad = txtAdSoyad.Text;
            string email = txtEmail.Text;
            string takim = cmbTakimlar.SelectedItem.ToString();
            string stad = cmbStadlar.SelectedItem.ToString();
            int biletSayisi = (int)numBiletSayisi.Value;

            // Biletleri satın alma işlemlerini burada yapabilirsiniz
            // Örneğin, bir veritabanına kaydedebilir veya bir API'ye gönderebilirsiniz

            // Satın alınan biletleri doğrulayın ve kullanıcıya geri bildirim verin
            string mesaj = $"Sayın {adSoyad}, {biletSayisi} adet maç bileti başarıyla satın alındı!\n" +
                $"Takım: {takim}\n" +
                $"Stad: {stad}\n" +
                $"E-posta: {email}";

            MessageBox.Show(mesaj, "Maç Bileti Satın Alma", MessageBoxButtons.OK, MessageBoxIcon.Information);

            // Formu sıfırla
            TemizleForm();
        }

        private void TemizleForm()
        {
            txtAdSoyad.Text = "";
            txtEmail.Text = "";
            cmbTakimlar.SelectedIndex = 0;
            cmbStadlar.SelectedIndex = 0;
            numBiletSayisi.Value = 1;
        }
    }
}

