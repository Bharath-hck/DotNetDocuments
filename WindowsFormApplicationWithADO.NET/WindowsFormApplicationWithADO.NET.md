# Windows Form Application

In this chapter, we will learn about windows form application.

### Populate DataGridView with Data Table 

```cs
private void GetStudentDetails()
{
    try
    {
        string ConnectionString = @"data source=localhost; database=StudentDB; user id=sa; password=admin@123";

        using (SqlConnection connection = new SqlConnection(ConnectionString))
        {
            SqlCommand cmd = new SqlCommand("spGetStudents", connection)
            {
                CommandType = CommandType.StoredProcedure
            };

            connection.Open();
            SqlDataReader sdr = cmd.ExecuteReader();

            DataTable dt = new DataTable();
            dt.Columns.Add("Id");
            dt.Columns.Add("Name");
            dt.Columns.Add("EmailID");
            dt.Columns.Add("Mobile");

            while (sdr.Read())
            {
                DataRow row = dt.NewRow();
                row["Id"] = sdr["Id"];
                row["Name"] = sdr["Name"];
                row["EmailID"] = sdr["Email"];
                row["Mobile"] = sdr["Mobile"];
                
                dt.Rows.Add(row);
            }

            dataGridView_StudentDetails.DataSource = dt;
            sdr.Close();                   
        }
    }
    catch (Exception ex)
    {
        MessageBox.Show($"Exception Occurred: {ex.Message}");
    }            
}
```

### Populate DataGridView with SQL Data Adapter

```cs
private void GetStudentDetailsUsingAdapter()
{
    try
    {
        string ConnectionString = @"data source=localhost; database=StudentDB; user id=sa; password=admin@123";

        using (SqlConnection connection = new SqlConnection(ConnectionString))
        {
            SqlDataAdapter da = new SqlDataAdapter("spGetStudents", connection);
            da.SelectCommand.CommandType = CommandType.StoredProcedure;               

            DataTable dt = new DataTable();
            dt.Columns.Add("Id");
            dt.Columns.Add("Name");
            dt.Columns.Add("EmailID");
            dt.Columns.Add("Mobile");

            da.Fill(dt);

            dataGridView_StudentDetails.DataSource = dt;
        }
    }
    catch (Exception ex)
    {
        MessageBox.Show($"Exception Occurred: {ex.Message}");
    }
}
```