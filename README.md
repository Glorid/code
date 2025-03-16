# code
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
    private void Main_Load(object sender, EventArgs e)<br>
    {<br>

    
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
