# SQL_LinqAdvanced
LinqAdvanced

///////////

using EfCoreDemo.Models;
using Microsoft.EntityFrameworkCore;
using System;
using System.Linq;

namespace EfCoreDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            var db = new ApplicationDbContext();
            db.Database.EnsureDeleted(); // WE DELETE THE OLD db IF EXISTS
            db.Database.EnsureCreated(); ///WE create the DB with the new model

            db.Database.ExecuteSqlRaw("Update Songs SET ModifiedOn = GETDATE()");
            db.Songs.Where(x => x.Id <= 10);
            db.Songs.ExecuteRaw("SELECT * FROM Songs WHERE Id <= 10");
        }
    }
}
