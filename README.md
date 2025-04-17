# code
Вставить в консоль<br>
Scaffold-DbContext "Server=;Database=;Uid=;Pwd=" Pomelo.EntityFrameworkCore.MySql -OutputDir Models -f 


public class UserController<br>
{<br>
    private Ispr2438BondaevInKyrsa4Context _dbContext; <br>
    public UserController()<br>
    {<br>
        _dbContext = new Ispr2438BondaevInKyrsa4Context(); <br>
    }<br>
    public Authorization? Authorize(string login, string password)<br>
    {<br>
        return _dbContext.Authorizations<br>
        .Include(u => u.Type)<br>
            .FirstOrDefault(u => u.Login == login && u.Password == password);<br>
    }<br>
}<br>

public UserController _userController {  get; set; } = new ();<br>
private void AutorizBtn_Click(object sender, EventArgs e)<br>
{<br>
string login = LoginTb.Text;<br>
string password = PasswordTb.Text; <br>
try<br>
{<br>
Client? client = _userController.Authorize(login, password);<br>
if (client == null)<br>
{ <br>
switch (client.TypeId)<br>
{<br>
case 4: <br>
new Zakaz4ikForm().Show();<br>
break;<br>
case 2:<br>
new MainForm().Show();<br>
break; <br>
default: MessageBox.Show("Роль не поддерживается."); <br>
return;<br>
} this.Hide();<br>
} <br>
}<br>
catch (Exception ex) <br>
{ <br>
MessageBox.Show($"Ошибка: {ex.Message}"); <br>
}<br>

}<br>
<br>
private Ispr2438BondaevInKyrsa4Context _dbContext; <br>
    public Main()<br>
    {<br>
        InitializeComponent();<br>
        _dbContext = new Ispr2438BondaevInKyrsa4Context();<br>
        LoadData();<br>
    }<br>
    private void LoadData()<br>
    {<br>
        var jobTitles = _dbContext.JobTitles.ToList();<br>
        dataGridView1.DataSource = jobTitles;<br>
    }<br>
    

    
<br>
    private void addBtn_Click(object sender, EventArgs e)<br>
    {<br>
<br>
        var jobTitle = new JobTitle { NameJob = addTb.Text };<br>
        _dbContext.JobTitles.Add(jobTitle);<br>
        _dbContext.SaveChanges();<br>
        LoadData(); // Обновляем DataGridView<br>
    }<br>
<br>
    private void delBtb_Click(object sender, EventArgs e)<br>
    {<br>
        if (dataGridView1.SelectedRows.Count > 0)<br>
        {<br>
            var selectedJobTitle = dataGridView1.SelectedRows[0].DataBoundItem as JobTitle;<br>
            if (selectedJobTitle != null)<br>
            {<br>
                _dbContext.JobTitles.Remove(selectedJobTitle);<br>
                _dbContext.SaveChanges();<br>
                LoadData(); // Обновляем DataGridView<br>
            }<br>
        }<br>
    }<br>
<br>
    private void backBtn_Click(object sender, EventArgs e)<br>
    {<br>
        Autoriz form = new Autoriz();<br>
        form.Show();<br>
        Hide();<br>
    }<br>
<br>
    private void label1_Click(object sender, EventArgs e)<br>
    {<br>
        Close();<br>
    }<br>
}<br>
