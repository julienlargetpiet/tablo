#include <iostream>
#include <vector>
#include <fstream>

bool can_be_nb(std::string &x) {
  const unsigned int n = x.length();
  std::string numeric_v = "0123456789";
  if (x[0] == '.' || x[n - 1] == '.') {
    return 0;
  };
  bool alrd_point = 0;
  unsigned int i2;
  char cur_chr;
  for (unsigned int i = 0; i < n; ++i) {
    if (x[i] == '.') {
      if (!alrd_point) {
        alrd_point = 1;
      } else {
        return 0;
      };
    } else {
      cur_chr = x[i];
      i2 = 0;
      while (i2 < 10) {
        if (cur_chr == numeric_v[i2]) {
          break;
        };
        i2 += 1;
      };
      if (i2 == 10) {
        return 0;
      };
    };
  };
  return 1;
};

bool can_be_flt_dbl(std::string &x) {
  const unsigned int n = x.length();
  std::string numeric_v = "0123456789";
  if (x[0] == '.' || x[n - 1] == '.') {
    return 0;
  };
  bool alrd_point = 0;
  unsigned int i2;
  char cur_chr;
  for (unsigned int i = 0; i < n; ++i) {
    if (x[i] == '.') {
      if (!alrd_point) {
        alrd_point = 1;
      } else {
        return 0;
      };
    } else {
      cur_chr = x[i];
      i2 = 0;
      while (i2 < 10) {
        if (cur_chr == numeric_v[i2]) {
          break;
        };
        i2 += 1;
      };
      if (i2 == 10) {
        return 0;
      };
    };
  };
  if (alrd_point) {
    return 1;
  } else {
    return 0;
  };
};

class Dataframe{
  private:
    
    unsigned int nrow = 0;
    unsigned int ncol = 0;
  
    std::vector<std::string> str_v = {};
    std::vector<char> chr_v = {};
    std::vector<bool> bool_v = {};
    std::vector<int> int_v = {};
    std::vector<unsigned int> uint_v = {};
    std::vector<double> dbl_v = {};
   
    std::vector<int> pre_str_v = {};
    std::vector<unsigned int> pre_chr_v = {};

    std::vector<std::vector<unsigned int>> matr_idx = {{}, {}, {}, {}, {}, {}};
    std::vector<std::string> name_v = {};
    std::vector<std::string> name_v_row = {};
    std::vector<unsigned int> longest_v = {};

    std::vector<const char*> type_refv = {};
    std::vector<std::vector<std::string>> tmp_val_refv = {};

    void longest_determine() {
      unsigned int i;
      unsigned int i2;
      if (name_v.size() > 0) {
        for (i = 0; i < ncol; ++i) {
          longest_v.push_back(name_v[i].length());
        };
      } else {
        longest_v.resize(ncol, 0);
      }; 
      for (i = 0; i < ncol; ++i) {
        for (i2 = 0; i2 < nrow; ++i2) {
          if (tmp_val_refv[i][i2].length() > longest_v[i]) {
            longest_v[i] = tmp_val_refv[i][i2].length();
          };
        };
      };
    };

  public:
    
    void readf(std::string &file_name, char delim = ',', bool header_name = 1, char str_context_begin = '\'', char str_context_end = '\'') {
      std::string currow;
      std::string cur_str = "";
      std::fstream readfile(file_name);
      getline(readfile, currow);
      ncol = 1;
      std::vector<std::string> ex_vec = {};
      std::vector<unsigned int> matr_unknown_vec = {};
      unsigned int i = 0;
      unsigned int verif_ncol;
      unsigned int max_lngth;
      bool str_cxt = 0;
      if (header_name) {
        while (i < currow.length()) {
          if (currow[i] == delim & !str_cxt) {
            if (i == 0) {
              max_lngth = 2;
              name_v.push_back("NA");
            } else if (currow[i - 1] == delim) {
              max_lngth = 2;
              name_v.push_back("NA");
            } else {
              max_lngth = cur_str.length();
              name_v.push_back(cur_str);
            };
            tmp_val_refv.push_back(ex_vec);
            ncol += 1;
            cur_str = "";
            longest_v.push_back(max_lngth);
          } else if (currow[i] == str_context_begin) {
            str_cxt = 1; 
          } else if (currow[i] == str_context_end) {
            str_cxt = 0;
          } else {
            cur_str.push_back(currow[i]);
          };
          i += 1;
        };
        if (currow[i - 1] == delim) {
          max_lngth = 2;
          name_v.push_back("NA");
        } else {
          max_lngth = cur_str.length();
          name_v.push_back(cur_str);
        };
        tmp_val_refv.push_back(ex_vec);
        cur_str = "";
        longest_v.push_back(max_lngth);
      } else {
        while (i < currow.length()) {
          if (currow[i] == delim & !str_cxt) {
            if (i == 0) {
              max_lngth = 2;
            } else if (currow[i - 1] == delim) {
              max_lngth = 2;
            } else {
              max_lngth = cur_str.length();
              ex_vec.push_back(cur_str);
              tmp_val_refv.push_back(ex_vec);
              ex_vec = {};
            };
            ncol += 1;
            cur_str = "";
            longest_v.push_back(max_lngth);
          } else if (currow[i] == str_context_begin) {
            str_cxt = 1;
          } else if (currow[i] == str_context_end) {
            str_cxt = 0;
          } else {
            cur_str.push_back(currow[i]);
          };
          i += 1;
        };
        if (currow[i - 1] == delim) {
          max_lngth = 2;
        } else {
          max_lngth = cur_str.length();
          ex_vec.push_back(cur_str);
          tmp_val_refv.push_back(ex_vec);
          ex_vec = {};
        };
        cur_str = "";
        longest_v.push_back(max_lngth);
        nrow += 1;
      };
      type_refv.reserve(ncol);
      while (getline(readfile, currow)) {
        verif_ncol = 1;
        str_cxt = 0;
        i = 0;
        while (i < currow.length()) {
          if (currow[i] == delim & !str_cxt) {
            if (i == 0) {
              if (longest_v[verif_ncol - 1] < 2) {
                longest_v[verif_ncol - 1] = 2;
              };
              tmp_val_refv[0].push_back("NA");
            } else if (currow[i - 1] == delim) {
              if (longest_v[verif_ncol - 1] < 2) {
                longest_v[verif_ncol - 1] = 2;
              };
              tmp_val_refv[verif_ncol - 1].push_back("NA");
            } else {
              if (longest_v[verif_ncol - 1] < cur_str.length()) {
                longest_v[verif_ncol - 1] = cur_str.length();
              };
              tmp_val_refv[verif_ncol - 1].push_back(cur_str);
            };
            cur_str = "";
            verif_ncol += 1;
          } else if (currow[i] == str_context_begin) {
            str_cxt = 1;
          } else if (currow[i] == str_context_end) {
            str_cxt = 0;
          } else {
            cur_str.push_back(currow[i]);
          };
          i += 1;
        };
        if (currow[i - 1] == delim) {
          if (longest_v[verif_ncol - 1] < 2) {
            longest_v[verif_ncol - 1] = 2;
          };
          tmp_val_refv[verif_ncol - 1].push_back("0");
        } else {
          if (longest_v[verif_ncol - 1] < cur_str.length()) {
            longest_v[verif_ncol - 1] = cur_str.length();
          };
          tmp_val_refv[verif_ncol - 1].push_back(cur_str);
        };
        cur_str = "";
        if (verif_ncol != ncol) {
          std::cout << "column number problem at row: " << nrow << "\n";
          reinitiate();
          return;
        };
        nrow += 1;
      };
      type_classification();
    };

    void type_classification() {
      unsigned int i;
      unsigned int i2;
      unsigned int n;
      bool is_nb;
      bool is_flt_dbl;
      bool is_unsigned = 1;
      bool is_bool = 1;
      std::string cur_str;
      std::string cur_str2;
      for (i = 0; i < ncol; ++i) {
        i2 = 0;
        while (i2 < nrow) {
          cur_str = tmp_val_refv[i][i2];
          cur_str2 = cur_str;
          if (cur_str[0] == '-' & cur_str.length() > 1) {
            cur_str2.erase(cur_str2.begin());
          };
          is_nb = can_be_nb(cur_str2);
          if (!is_nb) {
            if (cur_str.length() > 1) {
              type_refv.push_back(typeid(std::string).name());
              matr_idx[0].push_back(i);
              break;
            };
          } else {
            is_flt_dbl = can_be_flt_dbl(cur_str2);
            if (is_flt_dbl) {
              type_refv.push_back(typeid(double).name());
              matr_idx[5].push_back(i);
              break;
            };
            if (is_unsigned) {
              if (cur_str[0] == '-') {
                is_unsigned = 0;
              };
            };
            if (is_bool) {
              if (cur_str != "0" & cur_str != "1") {
                is_bool = 0;
              };
            };
          };
          i2 += 1;
        };
        if (i2 == nrow) {
          if (!is_nb) {
            type_refv.push_back(typeid(char).name());
            matr_idx[1].push_back(i);
          } else if (is_bool) {
            type_refv.push_back(typeid(bool).name());
            matr_idx[2].push_back(i);
          } else if (!is_unsigned) {
            type_refv.push_back(typeid(int).name());
            matr_idx[3].push_back(i);
          } else {
            type_refv.push_back(typeid(unsigned int).name());
            matr_idx[4].push_back(i);
          };
        };
      };
      for (i = 0; i < ncol; ++i) {
        if (type_refv[i] == typeid(std::string).name()) {
          for (i2 = 0; i2 < nrow; ++i2) {
            cur_str = tmp_val_refv[i][i2];
            str_v.push_back(cur_str);
          };
        } else if (type_refv[i] == typeid(char).name()) {
          for (i2 = 0; i2 < nrow; ++i2) {
            cur_str = tmp_val_refv[i][i2];
            chr_v.push_back(cur_str[0]);
          };
        } else if (type_refv[i] == typeid(bool).name()) {
          for (i2 = 0; i2 < nrow; ++i2) {
            cur_str = tmp_val_refv[i][i2];
            bool_v.push_back(std::stoi(cur_str));
          };
        } else if (type_refv[i] == typeid(int).name()) {
          for (i2 = 0; i2 < nrow; ++i2) {
            cur_str = tmp_val_refv[i][i2];
            int_v.push_back(std::stoi(cur_str));
          };
        } else if (type_refv[i] == typeid(unsigned int).name()) {
          for (i2 = 0; i2 < nrow; ++i2) {
            cur_str = tmp_val_refv[i][i2];
            uint_v.push_back(std::stoi(cur_str));
          };
        };
      };
    };
 
    void display() {
      unsigned int i2;
      unsigned int i3;
      unsigned int i4;
      unsigned int max_nblngth = std::to_string(nrow).length();
      for (i2 = 0; i2 < max_nblngth + 2; ++i2) {
        std::cout << " ";
      };
      std::string cur_str;
      bool is_found;
      for (i2 = 0; i2 < ncol; ++i2) {
        if (type_refv[i2] == typeid(std::string).name()) {
          cur_str = "<str>";
          if (longest_v[i2] < 5) {
            longest_v[i2] = 5;
          };
        } else if (type_refv[i2] == typeid(char).name()) {
          cur_str = "<char>";
          if (longest_v[i2] < 6) {
            longest_v[i2] = 6;
          };
        } else if (type_refv[i2] == typeid(bool).name()) {
          cur_str = "<bool>";
          if (longest_v[i2] < 6) {
            longest_v[i2] = 6;
          };
        } else if (type_refv[i2] == typeid(int).name()) {
          cur_str = "<int>";
          if (longest_v[i2] < 5) {
            longest_v[i2] = 5;
          };
        } else if (type_refv[i2] == typeid(unsigned int).name()) {
          cur_str = "<uint>";
          if (longest_v[i2] < 6) {
            longest_v[i2] = 6;
          };
        } else if (type_refv[i2] == typeid(double).name()) {
          cur_str = "<double>";
          if (longest_v[i2] < 8) {
            longest_v[i2] = 8;
          };
        };
        std::cout << cur_str << " ";  
        for (i4 = cur_str.length(); i4 < longest_v[i2]; ++i4) {
          std::cout << " ";
        };
      };
      std::cout << "\n";
      for (i2 = 0; i2 < max_nblngth + 2; ++i2) {
        std::cout << " ";
      };
      if (name_v.size() > 0) {
        for (i2 = 0; i2 < ncol; ++i2) {
          cur_str = name_v[i2];
          std::cout << cur_str << " ";  
          for (i4 = cur_str.length(); i4 < longest_v[i2]; ++i4) {
            std::cout << " ";
          };
        };
      } else {
        for (i2 = 0; i2 < ncol; ++i2) {
          cur_str = "[" + std::to_string(i2) + "]";
          std::cout << cur_str << " ";
          for (i4 = cur_str.length(); i4 < longest_v[i2]; ++i4) {
            std::cout << " ";
          };
        };
      };
      std::cout << "\n";
      for (unsigned int i = 0; i < nrow; ++i) {
        std::cout << ":" << i << ": ";
        for (i3 = std::to_string(i).length(); i3 < max_nblngth; ++i3) {
          std::cout << " ";
        };
        for (i2 = 0; i2 < ncol; ++i2) {
          cur_str = tmp_val_refv[i2][i];
          std::cout << cur_str << " ";
          for (i3 = cur_str.length(); i3 < longest_v[i2]; ++i3) {
            std::cout << " ";
          };
        };
        std::cout << "\n";
      };
    };

    void reinitiate() {
     
      nrow = 0;
      ncol = 0;
 
      str_v = {};
      chr_v = {};
      bool_v = {};
      int_v = {};
      uint_v = {};
      dbl_v = {};
   
      pre_str_v = {};
      pre_chr_v = {};

      matr_idx = {{}, {}, {}, {}, {}, {}};
      name_v = {};
      name_v_row = {};
      longest_v = {};

      type_refv = {};
      tmp_val_refv = {};

    };

    template <typename T> void name_colint(std::vector<int> rows, std::string colname, std::vector<T> &rtn_v) {
      if (name_v.size() == 0) {
        std::cout << "no column names\n";
        reinitiate();
        return;
      };
      unsigned int x = 0;
      while (colname != name_v[x]) {
        x += 1;
      };
      rtn_v.reserve(nrow);
      unsigned int i = 2;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      i2 = 0;
      bool is_found = 0;
      while (!is_found) {
        while (i2 < matr_idx[i].size()) {
          if (x == matr_idx[i][i2]) {
            is_found = 1;
            break;
          };
          i2 += 1;
        };
        i += 1;
      };
      i -= 1;
      i2 = nrow * i2;
      if (i == 2) {
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(bool_v[i2 + rows[i]]);
        };
      } else if (i == 3) {
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(int_v[i2 + rows[i]]);
        };
      } else if (i == 4) {
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(uint_v[i2 + rows[i]]);
        };
      } else if (i == 5) {
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(dbl_v[i2 + rows[i]]);
        };
      };
    };

    template <typename T> void idx_colint(std::vector<int> rows, unsigned int x, std::vector<T> &rtn_v) {
      rtn_v.reserve(nrow);
      unsigned int i = 2;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      i2 = 0;
      bool is_found = 0;
      while (!is_found) {
        while (i2 < matr_idx[i].size()) {
          if (x == matr_idx[i][i2]) {
            is_found = 1;
            break;
          };
          i2 += 1;
        };
        i += 1;
      };
      i -= 1;
      i2 = nrow * i2;
      if (i == 2) {
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(bool_v[i2 + rows[i]]);
        };
      } else if (i == 3) {
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(int_v[i2 + rows[i]]);
        };
      } else if (i == 4) {
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(uint_v[i2 + rows[i]]);
        };
      } else if (i == 5) {
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(dbl_v[i2 + rows[i]]);
        };
      };
    };

    void name_colstr(std::vector<int> rows, std::string colname, std::vector<std::string> &rtn_v) {
      if (name_v.size() == 0) {
        std::cout << "no column names\n";
        reinitiate();
        return;
      };
      unsigned int x = 0;
      while (colname != name_v[x]) {
        x += 1;
      };
      rtn_v.reserve(nrow);
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      i2 = 0;
      while (i2 < matr_idx[0].size()) {
        if (x == matr_idx[0][i2]) {
          break;
        };
        i2 += 1;
      };
      i2 = nrow * i2;
      for (i = 0; i < rows.size(); ++i) {
        rtn_v.push_back(str_v[i2 + rows[i]]);
      };
    };

    void idx_colstr(std::vector<int> rows, unsigned int x, std::vector<std::string> &rtn_v) {
      rtn_v.reserve(nrow);
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      i2 = 0;
      while (i2 < matr_idx[0].size()) {
        if (x == matr_idx[0][i2]) {
          break;
        };
        i2 += 1;
      };
      i2 = nrow * i2;
      for (i = 0; i < rows.size(); ++i) {
        rtn_v.push_back(str_v[i2 + rows[i]]);
      };
    };

    void name_colchr(std::vector<int> rows, std::string colname, std::vector<char> &rtn_v) {
      if (name_v.size() == 0) {
        std::cout << "no column names\n";
        reinitiate();
        return;
      };
      unsigned int x = 0;
      while (colname != name_v[x]) {
        x += 1;
      };
      rtn_v.reserve(nrow);
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      i2 = 0;
      while (i2 < matr_idx[1].size()) {
        if (x == matr_idx[1][i2]) {
          break;
        };
        i2 += 1;
      };
      i2 = nrow * i2;
      for (i = 0; i < rows.size(); ++i) {
        rtn_v.push_back(chr_v[i2 + rows[i]]);
      };
    };

    void idx_colchr(std::vector<int> rows, unsigned int x, std::vector<char> &rtn_v) {
      rtn_v.reserve(nrow);
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      i2 = 0;
      while (i2 < matr_idx[1].size()) {
        if (x == matr_idx[1][i2]) {
          break;
        };
        i2 += 1;
      };
      i2 = nrow * i2;
      for (i = 0; i < rows.size(); ++i) {
        rtn_v.push_back(chr_v[i2 + rows[i]]);
      };
    };

    template <typename T> void name_matrint(std::vector<int> rows, std::vector<std::string> x_v, std::vector<std::vector<T>> &rtn_matr) {
      std::vector<T> rtn_v;
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      bool is_found;
      unsigned int x;
      if (name_v.size() == 0) {
        std::cout << "There are no column names\n";
        reinitiate();
        return;
      };
      for (std::string cur_name : x_v) {
        x = 0;
        while (cur_name != name_v[x]) {
          x += 1;
        };
        rtn_v = {};
        rtn_v.reserve(nrow);
        i = 2;
        i2 = 0;
        is_found = 0;
        while (!is_found) {
          while (i2 < matr_idx[i].size()) {
            if (x == matr_idx[i][i2]) {
              is_found = 1;
              break;
            };
            i2 += 1;
          };
          i += 1;
        };
        i -= 1;
        i2 = nrow * i2;
        if (i == 2) {
          for (i = 0; i < rows.size(); ++i) {
            rtn_v.push_back(bool_v[i2 + rows[i]]);
          };
        } else if (i == 3) {
          for (i = 0; i < rows.size(); ++i) {
            rtn_v.push_back(int_v[i2 + rows[i]]);
          };
        } else if (i == 4) {
          for (i = 0; i < rows.size(); ++i) {
            rtn_v.push_back(uint_v[i2 + rows[i]]);
          };
        } else if (i == 5) {
          for (i = 0; i < rows.size(); ++i) {
            rtn_v.push_back(dbl_v[i2 + rows[i]]);
          };
        };
        rtn_matr.push_back(rtn_v);
      };
    };

    template <typename T> void idx_matrint(std::vector<int> rows, std::vector<unsigned int> x_v, std::vector<std::vector<T>> &rtn_matr) {
      std::vector<T> rtn_v;
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      bool is_found;
      for (unsigned int x : x_v) {
        rtn_v = {};
        rtn_v.reserve(nrow);
        i = 2;
        i2 = 0;
        is_found = 0;
        while (!is_found) {
          while (i2 < matr_idx[i].size()) {
            if (x == matr_idx[i][i2]) {
              is_found = 1;
              break;
            };
            i2 += 1;
          };
          i += 1;
        };
        i -= 1;
        i2 = nrow * i2;
        if (i == 2) {
          for (i = 0; i < rows.size(); ++i) {
            rtn_v.push_back(bool_v[i2 + rows[i]]);
          };
        } else if (i == 3) {
          for (i = 0; i < rows.size(); ++i) {
            rtn_v.push_back(int_v[i2 + rows[i]]);
          };
        } else if (i == 4) {
          for (i = 0; i < rows.size(); ++i) {
            rtn_v.push_back(uint_v[i2 + rows[i]]);
          };
        } else if (i == 5) {
          for (i = 0; i < rows.size(); ++i) {
            rtn_v.push_back(dbl_v[i2 + rows[i]]);
          };
        };
        rtn_matr.push_back(rtn_v);
      };
    };

    void name_matrstr(std::vector<int> rows, std::vector<std::string> x_v, std::vector<std::vector<std::string>> &rtn_matr) {
      std::vector<std::string> rtn_v;
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      unsigned int x;
      if (name_v.size() == 0) {
        std::cout << "There are no column names\n";
        reinitiate();
        return;
      };
      for (std::string cur_name : x_v) {
        x = 0;
        while (cur_name != name_v[x]) {
          x += 1;
        };
        rtn_v = {};
        rtn_v.reserve(nrow);
        i2 = 0;
        while (i2 < matr_idx[0].size()) {
          if (x == matr_idx[0][i2]) {
            break;
          };
          i2 += 1;
        };
        i2 = nrow * i2;
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(str_v[i2 + rows[i]]);
        }; 
        rtn_matr.push_back(rtn_v);
      };
    };

    void idx_matrstr(std::vector<int> rows, std::vector<unsigned int> x_v, std::vector<std::vector<std::string>> &rtn_matr) {
      std::vector<std::string> rtn_v;
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      for (unsigned int x : x_v) {
        rtn_v = {};
        rtn_v.reserve(nrow);
        i = 2;
        i2 = 0;
        while (i2 < matr_idx[0].size()) {
          if (x == matr_idx[0][i2]) {
            break;
          };
          i2 += 1;
        };
        i2 = nrow * i2;
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(str_v[i2 + rows[i]]);
        };
        rtn_matr.push_back(rtn_v);
      };
    };

    void name_matrchr(std::vector<int> rows, std::vector<std::string> x_v, std::vector<std::vector<char>> &rtn_matr) {
      std::vector<char> rtn_v;
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      unsigned int x;
      if (name_v.size() == 0) {
        std::cout << "There are no column names\n";
        reinitiate();
        return;
      };
      for (std::string cur_name : x_v) {
        x = 0;
        while (cur_name != name_v[x]) {
          x += 1;
        };
        rtn_v = {};
        rtn_v.reserve(nrow);
        i2 = 0;
        while (i2 < matr_idx[1].size()) {
          if (x == matr_idx[1][i2]) {
            break;
          };
          i2 += 1;
        };
        i2 = nrow * i2;
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(chr_v[i2 + rows[i]]);
        }; 
        rtn_matr.push_back(rtn_v);
      };
    };

    void idx_matrchr(std::vector<int> rows, std::vector<unsigned int> x_v, std::vector<std::vector<char>> &rtn_matr) {
      std::vector<char> rtn_v;
      unsigned int i;
      unsigned int i2;
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < nrow; ++i2) {
          rows.push_back(i2);
        };
      };
      for (unsigned int x : x_v) {
        rtn_v = {};
        rtn_v.reserve(nrow);
        i = 2;
        i2 = 0;
        while (i2 < matr_idx[1].size()) {
          if (x == matr_idx[1][i2]) {
            break;
          };
          i2 += 1;
        };
        i2 = nrow * i2;
        for (i = 0; i < rows.size(); ++i) {
          rtn_v.push_back(chr_v[i2 + rows[i]]);
        };
        rtn_matr.push_back(rtn_v);
      };
    };

    std::vector<std::vector<std::string>> get_tmp_val_refv() {
      return tmp_val_refv;
    };

    unsigned int get_nrow() {
      return nrow;
    };

    unsigned int get_ncol() {
      return ncol;
    };

    void name_dataframe(std::vector<int> &rows, std::vector<std::string> &name_cols, Dataframe &cur_obj) {
      unsigned int i2;
      unsigned int max_nrow = cur_obj.get_nrow();
      unsigned int max_ncol = cur_obj.get_ncol();
      std::vector<std::string> objcname = cur_obj.get_colname();
      nrow = rows.size();
      ncol = name_cols.size();
      if (objcname.size() == 0) {
        std::cout << "The dataframe has no column name\n";
        reinitiate();
        return;
      };
      std::vector<int> cols = {};
      for (std::string valstr : objcname) {
        for (i2 = 0; i2 < ncol; ++i2) {
          if (valstr == objcname[i2]) {
            cols.push_back(i2);
            break;
          };
        };
      };
      std::vector<std::vector<std::string>> cur_tmp = cur_obj.get_tmp_val_refv();
      std::vector<std::string> cur_v = {};
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < max_nrow; ++i2) {
          rows.push_back(i2);
        };
        nrow = max_nrow;
      };
      if (cols[0] == -1) {
        cols.pop_back();
        for (i2 = 0; i2 < max_ncol; ++i2) {
          cols.push_back(i2);
        };
        ncol = max_ncol;
      };
      for (unsigned int i : cols) {
        cur_v = {};
        for (i2 = 0; i2 < nrow; ++i2) {
          cur_v.push_back(cur_tmp[i][rows[i2]]);  
        };
        tmp_val_refv.push_back(cur_v);
      };
      type_classification();
      name_v = cur_obj.get_colname();
      name_v_row = cur_obj.get_rowname(); 
      longest_determine();
    };

    void idx_dataframe(std::vector<int> &rows, std::vector<int> &cols, Dataframe &cur_obj) {
      unsigned int i2;
      unsigned int max_nrow = cur_obj.get_nrow();
      unsigned int max_ncol = cur_obj.get_ncol();
      nrow = rows.size();
      ncol = cols.size();
      std::vector<std::vector<std::string>> cur_tmp = cur_obj.get_tmp_val_refv();
      std::vector<std::string> cur_v = {};
      if (rows[0] == -1) {
        rows.pop_back();
        for (i2 = 0; i2 < max_nrow; ++i2) {
          rows.push_back(i2);
        };
        nrow = max_nrow;
      };
      if (cols[0] == -1) {
        cols.pop_back();
        for (i2 = 0; i2 < max_ncol; ++i2) {
          cols.push_back(i2);
        };
        ncol = max_ncol;
      };
      for (unsigned int i : cols) {
        cur_v = {};
        for (i2 = 0; i2 < nrow; ++i2) {
          cur_v.push_back(cur_tmp[i][rows[i2]]);  
        };
        tmp_val_refv.push_back(cur_v);
      };
      type_classification();
      name_v = cur_obj.get_colname();
      name_v_row = cur_obj.get_rowname(); 
      longest_determine();
    };

    void writef(std::string &file_name, char delim = ',', bool header_name = 1, char str_context_bgn = '\'', char str_context_end = '\'') {
      unsigned int i2;
      unsigned int i3;
      std::fstream outfile(file_name, std::ios::out);
      std::string cur_str;
      if (header_name) {
        i2 = 0;
        while (i2 + 1 < ncol) {
          outfile << name_v[i2];
          outfile << delim;
          i2 += 1;
        };
        outfile << name_v[i2];
        outfile << "\n";
      };
      for (unsigned int i = 0; i < nrow; ++i) {
        i2 = 0;
        while (i2 + 1 < ncol) {
          cur_str = tmp_val_refv[i2][i];
          if (type_refv[i2] == typeid(std::string).name()) {
            for (i3 = 0; i3 < cur_str.length(); ++i3) {
              if (cur_str[i3] == delim) {
                cur_str.insert(0, 1, str_context_bgn);
                cur_str.push_back(str_context_end);
                break;
              };
            };
          } else if (cur_str[0] == delim) {
            cur_str.insert(0, 1, str_context_bgn);
            cur_str.push_back(str_context_end);
          };
          outfile << cur_str;
          i2 += 1;
          outfile << delim;
        };
        cur_str = tmp_val_refv[i2][i];
        if (type_refv[i2] == typeid(std::string).name()) {
          for (i3 = 0; i3 < cur_str.length(); ++i3) {
            if (cur_str[i3] == delim) {
              cur_str.insert(0, 1, str_context_bgn);
              cur_str.push_back(str_context_end);
              break;
            };
          };
        } else if (cur_str[0] == delim) {
          cur_str.insert(0, 1, str_context_bgn);
          cur_str.push_back(str_context_end);
        };
        outfile << cur_str;
        outfile << "\n";
      };
    };

    template <typename T> void replace_colint(std::vector<T> &x, unsigned int &colnb) {
      unsigned int i = 2;
      unsigned int i2;
      bool is_found = 0;
      while (!is_found) {
        i2 = 0;
        while (i2 < matr_idx[i].size()) {
          if (colnb == matr_idx[i][i2]) {
            is_found = 1;
            break;
          };
          i2 += 1;
        };
        i += 1;
      };
      i -= 1;
      i2 = nrow * i2;
      if (i == 2) {
        for (i = 0; i < nrow; ++i) {
          bool_v[i2 + i] = x[i];
          tmp_val_refv[colnb][i] = std::to_string(x[i]);
        };
      } else if (i == 3) {
        for (i = 0; i < nrow; ++i) {
          int_v[i2 + i] = x[i];
          tmp_val_refv[colnb][i] = std::to_string(x[i]);
        };
      } else if (i == 4) {
        for (i = 0; i < nrow; ++i) {
          uint_v[i2 + i] = x[i];
          tmp_val_refv[colnb][i] = std::to_string(x[i]);
        };
      } else if (i == 5) {
        for (i = 0; i < nrow; ++i) {
          dbl_v[i2 + i] = x[i];
          tmp_val_refv[colnb][i] = std::to_string(x[i]);
        };
      };
    };

    void replace_colstr(std::vector<std::string> &x, unsigned int &colnb) {
      unsigned int i;
      unsigned int i2 = 0;
      while (1) {
        if (colnb == matr_idx[0][i2]) {
          break;
        };
        i2 += 1;
      };
      i2 = nrow * i2;
      for (i = 0; i < nrow; ++i) {
        str_v[i2 + i] = x[i];
        tmp_val_refv[colnb][i] = x[i];
      };
    };

    void replace_colchr(std::vector<char> &x, unsigned int &colnb) {
      unsigned int i;
      unsigned int i2 = 0;
      std::string cur_str;
      while (1) {
        if (colnb == matr_idx[1][i2]) {
          break;
        };
        i2 += 1;
      };
      i2 = nrow * i2;
      for (i = 0; i < nrow; ++i) {
        chr_v[i2 + i] = x[i];
        cur_str = "";
        cur_str.push_back(x[i]);
        tmp_val_refv[colnb][i] = cur_str;
      };
    };

    template <typename T> void add_colint(std::vector<T> &x, std::string name = "NA") {
      name_v.push_back(name);
      unsigned int i;
      std::vector<std::string> cur_v = {};
      if (typeid(T).name() == typeid(bool).name()) {
        matr_idx[2].push_back(ncol);
        type_refv.push_back(typeid(bool).name());
        for (i = 0; i < nrow; ++i) {
          bool_v.push_back(x[i]);
          cur_v.push_back(std::to_string(x[i]));
        };
      } else if (typeid(T).name() == typeid(int).name()) {
        matr_idx[3].push_back(ncol);
        type_refv.push_back(typeid(int).name());
        for (i = 0; i < nrow; ++i) {
          int_v.push_back(x[i]);
          cur_v.push_back(std::to_string(x[i]));
        };
      } else if (typeid(T).name() == typeid(unsigned int).name()) {
        matr_idx[4].push_back(ncol);
        type_refv.push_back(typeid(unsigned int).name());
        for (i = 0; i < nrow; ++i) {
          uint_v.push_back(x[i]);
          cur_v.push_back(std::to_string(x[i]));
        };
      } else if (typeid(T).name() == typeid(double).name()) {
        matr_idx[5].push_back(ncol);
        type_refv.push_back(typeid(double).name());
        for (i = 0; i < nrow; ++i) {
          dbl_v.push_back(x[i]);
          cur_v.push_back(std::to_string(x[i]));
        }; 
      };
      tmp_val_refv.push_back(cur_v);
      ncol += 1;
    };

    void add_colstr(std::vector<std::string> &x, std::string name = "NA") {
      name_v.push_back(name);
      unsigned int i;
      std::vector<std::string> cur_v = {};
      matr_idx[0].push_back(ncol);
      type_refv.push_back(typeid(std::string).name());
      for (i = 0; i < nrow; ++i) {
        str_v.push_back(x[i]);
        cur_v.push_back(x[i]);
      };
      tmp_val_refv.push_back(cur_v);
      ncol += 1;
    };

    void add_colchr(std::vector<char> &x, std::string name = "NA") {
      name_v.push_back(name);
      unsigned int i;
      std::vector<std::string> cur_v = {};
      matr_idx[1].push_back(ncol);
      type_refv.push_back(typeid(char).name());
      std::string cur_str;
      for (i = 0; i < nrow; ++i) {
        chr_v.push_back(x[i]);
        cur_str = "";
        cur_str.push_back(x[i]);
        cur_v.push_back(cur_str);
      };
      tmp_val_refv.push_back(cur_v);
      ncol += 1;
    };

    void rm_col(std::vector<unsigned int> &nbcolv) {
      unsigned int i;
      unsigned int i2;
      bool is_found;
      for (int nbcol : nbcolv) {
        if (nbcol >= ncol) {
          std::cout << "The column does not exist\n";
          return;
        };
        i = 0;
        i2;
        is_found = 0;
        while (!is_found) {
          i2 = 0;
          while (i2 < matr_idx[i].size()) {
            if (nbcol == matr_idx[i][i2]) {
              is_found = 1;
              break;
            };
            i2 += 1;
          };
          i += 1;
        };
        i-= 1;
        name_v.erase(name_v.begin() + nbcol);
        matr_idx[i].erase(matr_idx[i].begin() + i2);
        tmp_val_refv.erase(tmp_val_refv.begin() + nbcol);
        type_refv.erase(type_refv.begin() + nbcol);
        i2 = nrow * i2;
        if (i == 0) {
          str_v.erase(str_v.begin() + i2, str_v.begin() + i2 + nrow);
        } else if (i == 1) {
          chr_v.erase(chr_v.begin() + i2, chr_v.begin() + i2 + nrow);
        } else if (i == 2) {
          bool_v.erase(bool_v.begin() + i2, bool_v.begin() + i2 + nrow);
        } else if (i == 3) {
          int_v.erase(int_v.begin() + i2, int_v.begin() + i2 + nrow);
        } else if (i == 4) {
          uint_v.erase(uint_v.begin() + i2, uint_v.begin() + i2 + nrow);
        } else if (i == 5) {
          dbl_v.erase(dbl_v.begin() + i2, dbl_v.begin() + i2 + nrow);
        };
        ncol -= 1;
      };
    };

    void rm_row(std::vector<unsigned int> &x) {
      unsigned int i;
      unsigned int cnt = 0;
      std::vector<unsigned int> alrd_v = {0, 0, 0, 0, 0, 0};
      for (unsigned int i2 = nrow - 1; i2 > 0; --i2) {
        if (i2 == x[cnt]) {
          for (i = 0; i < ncol; ++i) {
            tmp_val_refv[i].erase(tmp_val_refv[i].begin() + i2);
            if (type_refv[i] == typeid(std::string).name()) {
              str_v.erase(str_v.begin() + alrd_v[0] * nrow + i2);
              alrd_v[0] += 1;
            } else if (type_refv[i] == typeid(char).name()) {
              chr_v.erase(chr_v.begin() + alrd_v[1] * nrow + i2);
              alrd_v[1] += 1;
            } else if (type_refv[i] == typeid(bool).name()) {
              bool_v.erase(bool_v.begin() + alrd_v[2] * nrow + i2);
              alrd_v[2] += 1;
            } else if (type_refv[i] == typeid(int).name()) {
              int_v.erase(int_v.begin() + alrd_v[3] * nrow + i2);
              alrd_v[3] += 1;
            } else if (type_refv[i] == typeid(unsigned int).name()) {
              uint_v.erase(uint_v.begin() + alrd_v[4] * nrow + i2);
              alrd_v[4] += 1;
            } else if (type_refv[i] == typeid(double).name()) {
              dbl_v.erase(dbl_v.begin() + alrd_v[5] * nrow + i2);
              alrd_v[5] += 1;
            };
          };
          nrow -= 1;
          cnt += 1;
        };
      };
    };

    void transform_inner(Dataframe &cur_obj, unsigned int &in_col, unsigned int &ext_col) {
      unsigned int i2;
      std::vector<std::vector<std::string>> cur_tmp = cur_obj.get_tmp_val_refv();
      std::vector<std::string> ext_colv = cur_tmp[ext_col];
      std::vector<std::string> in_colv = tmp_val_refv[in_col];
      std::string cur_val;
      const unsigned int ext_nrow = cur_obj.get_nrow();
      for (int i = nrow - 1; i >= 0; --i) {
        i2 = 0;
        cur_val = in_colv[i];
        while (i2 < ext_nrow) {
          if (cur_val == ext_colv[i2]) {
            break;
          };
          i2 += 1;
        };
        if (i2 == ext_nrow) {
          nrow -= 1;
          for (i2 = 0; i2 < ncol; ++i2) {
            tmp_val_refv[i2].erase(tmp_val_refv[i2].begin() + i);
            if (type_refv[i2] == typeid(std::string).name()) {
              str_v.erase(str_v.begin() + nrow * i2 + i);
            } else if (type_refv[i2] == typeid(char).name()) {
              chr_v.erase(chr_v.begin() + nrow * i2 + i);
            } else if (type_refv[i2] == typeid(bool).name()) {
              bool_v.erase(bool_v.begin() + nrow * i2 + i);
            } else if (type_refv[i2] == typeid(int).name()) {
              int_v.erase(int_v.begin() + nrow * i2 + i);
            } else if (type_refv[i2] == typeid(unsigned int).name()) {
              uint_v.erase(uint_v.begin() + nrow * i2 + i);
            } else if (type_refv[i2] == typeid(double).name()) {
              dbl_v.erase(dbl_v.begin() + nrow * i2 + i);
            };
          };
        };
      };
    };

    void transform_excluding(Dataframe &cur_obj, unsigned int &in_col, unsigned int &ext_col) {
      unsigned int i2;
      unsigned int i3;
      std::vector<std::vector<std::string>> cur_tmp = cur_obj.get_tmp_val_refv();
      std::vector<std::string> ext_colv = cur_tmp[ext_col];
      std::vector<std::string> in_colv = tmp_val_refv[in_col];
      std::string cur_val;
      const unsigned int ext_nrow = cur_obj.get_nrow();
      for (int i = nrow - 1; i >= 0; --i) {
        cur_val = in_colv[i];
        for (i2 = 0; i2 < ext_nrow; ++i2) {
          if (cur_val == ext_colv[i2]) {
            nrow -= 1;
            for (i3 = 0; i3 < ncol; ++i3) {
              tmp_val_refv[i3].erase(tmp_val_refv[i3].begin() + i);
              if (type_refv[i3] == typeid(std::string).name()) {
                str_v.erase(str_v.begin() + nrow * i3 + i);
              } else if (type_refv[i3] == typeid(char).name()) {
                chr_v.erase(chr_v.begin() + nrow * i3 + i);
              } else if (type_refv[i3] == typeid(bool).name()) {
                bool_v.erase(bool_v.begin() + nrow * i3 + i);
              } else if (type_refv[i3] == typeid(int).name()) {
                int_v.erase(int_v.begin() + nrow * i3 + i);
              } else if (type_refv[i3] == typeid(unsigned int).name()) {
                uint_v.erase(uint_v.begin() + nrow * i3 + i);
              } else if (type_refv[i3] == typeid(double).name()) {
                dbl_v.erase(dbl_v.begin() + nrow * i3 + i);
              };
            };
            break;
          };
        };
      };
    };

    void merge_inner(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2) {
      unsigned int ncol1 = obj1.get_ncol();
      unsigned int ncol2 = obj2.get_ncol();
      std::vector<std::string> cur_vstr;
      ncol = ncol1 + ncol2;
      const unsigned int nrow1 = obj1.get_nrow();
      const unsigned int nrow2 = obj2.get_nrow();
      unsigned int i;
      unsigned int i2;
      unsigned int i3;
      std::vector<std::string> name1 = obj1.get_colname();
      std::vector<std::string> name2 = obj2.get_colname();
      if (colname) {
        name_v.resize(ncol);
        if (name1.size() > 0) {
          for (i = 0; i < name1.size(); ++i) {
            name_v.push_back(name1[i]);
          };
        };
        if (name2.size() > 0) {
          for (i = 0; i < name2.size(); ++i) {
            name_v.push_back(name2[i]);
          };
        };
      };
      tmp_val_refv.resize(ncol);
      for (i = 0; i < ncol; ++i) {
        tmp_val_refv.push_back(cur_vstr);
      };
      std::vector<const char*> type1 = obj1.get_typecol();
      std::vector<const char*> type2 = obj2.get_typecol();
      type_refv.reserve(ncol);
      for (i = 0; i < ncol1; ++i) {
        type_refv.push_back(type1[i]);
      };
      for (i = 0; i < ncol2; ++i) {
        type_refv.push_back(type2[i]);
      };
      std::vector<std::vector<std::string>> tmp1 = obj1.get_tmp_val_refv();
      std::vector<std::vector<std::string>> tmp2 = obj2.get_tmp_val_refv();
      std::vector<std::string> col1 = tmp1[key1];
      std::vector<std::string> col2 = tmp2[key2];
      std::string cur_str;
      for (i = 0; i < nrow1; ++i) {
        cur_str = col1[i];
        for (i2 = 0; i2 < nrow2; ++i2) {
          if (cur_str == col2[i2]) {
            for (i3 = 0; i3 < ncol1; ++i3) {
              tmp_val_refv[i3].push_back(tmp1[i3][i]);
            };
            for (i3 = 0; i3 < ncol2; ++i3) {
              tmp_val_refv[ncol1 + i3].push_back(tmp2[i3][i2]);
            };
            nrow += 1;
            break;
          };
        };
      };
      longest_determine();
    };

    void merge_excluding(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2) {
      unsigned int ncol1 = obj1.get_ncol();
      unsigned int ncol2 = obj2.get_ncol();
      std::vector<std::string> cur_vstr;
      ncol = ncol1 + ncol2;
      const unsigned int nrow1 = obj1.get_nrow();
      const unsigned int nrow2 = obj2.get_nrow();
      unsigned int i;
      unsigned int i2;
      std::vector<std::string> name1 = obj1.get_colname();
      std::vector<std::string> name2 = obj2.get_colname();
      if (colname) {
        name_v.resize(ncol);
        if (name1.size() > 0) {
          for (i = 0; i < name1.size(); ++i) {
            name_v.push_back(name1[i]);
          };
        };
        if (name2.size() > 0) {
          for (i = 0; i < name2.size(); ++i) {
            name_v.push_back(name2[i]);
          };
        };
      };
      tmp_val_refv.resize(ncol);
      for (i = 0; i < ncol; ++i) {
        tmp_val_refv.push_back(cur_vstr);
      };
      std::vector<const char*> type1 = obj1.get_typecol();
      std::vector<const char*> type2 = obj2.get_typecol();
      type_refv.reserve(ncol);
      for (i = 0; i < ncol1; ++i) {
        type_refv.push_back(type1[i]);
      };
      for (i = 0; i < ncol2; ++i) {
        type_refv.push_back(type2[i]);
      };
      std::vector<std::vector<std::string>> tmp1 = obj1.get_tmp_val_refv();
      std::vector<std::vector<std::string>> tmp2 = obj2.get_tmp_val_refv();
      std::vector<std::string> col1 = tmp1[key1];
      std::vector<std::string> col2 = tmp2[key2];
      std::string cur_str;
      for (i = 0; i < nrow1; ++i) {
        i2 = 0;
        cur_str = col1[i];
        while (i2 < nrow2) {
          if (cur_str == col2[i2]) {
            break;
          };
         i2 += 1;
        };
        if (i2 == nrow2) {
          for (i2 = 0; i2 < ncol1; ++i2) {
            tmp_val_refv[i2].push_back(tmp1[i2][i]);
          };
          for (i2 = 0; i2 < ncol2; ++i2) {
            tmp_val_refv[i2 + ncol1].push_back("NA");
          };
          nrow += 1;
        };
      };
      longest_determine();
    };

    void merge_excluding_both(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2) {
      unsigned int ncol1 = obj1.get_ncol();
      unsigned int ncol2 = obj2.get_ncol();
      std::vector<std::string> cur_vstr;
      ncol = ncol1 + ncol2;
      const unsigned int nrow1 = obj1.get_nrow();
      const unsigned int nrow2 = obj2.get_nrow();
      unsigned int i;
      unsigned int i2;
      std::vector<std::string> name1 = obj1.get_colname();
      std::vector<std::string> name2 = obj2.get_colname();
      if (colname) {
        name_v.resize(ncol);
        if (name1.size() > 0) {
          for (i = 0; i < name1.size(); ++i) {
            name_v.push_back(name1[i]);
          };
        };
        if (name2.size() > 0) {
          for (i = 0; i < name2.size(); ++i) {
            name_v.push_back(name2[i]);
          };
        };
      };
      tmp_val_refv.resize(ncol);
      for (i = 0; i < ncol; ++i) {
        tmp_val_refv.push_back(cur_vstr);
      };
      std::vector<const char*> type1 = obj1.get_typecol();
      std::vector<const char*> type2 = obj2.get_typecol();
      type_refv.reserve(ncol);
      for (i = 0; i < ncol1; ++i) {
        type_refv.push_back(type1[i]);
      };
      for (i = 0; i < ncol2; ++i) {
        type_refv.push_back(type2[i]);
      };
      std::vector<std::vector<std::string>> tmp1 = obj1.get_tmp_val_refv();
      std::vector<std::vector<std::string>> tmp2 = obj2.get_tmp_val_refv();
      std::vector<std::string> col1 = tmp1[key1];
      std::vector<std::string> col2 = tmp2[key2];
      std::string cur_str;
      for (i = 0; i < nrow1; ++i) {
        i2 = 0;
        cur_str = col1[i];
        while (i2 < nrow2) {
          if (cur_str == col2[i2]) {
            break;
          };
         i2 += 1;
        };
        if (i2 == nrow2) {
          for (i2 = 0; i2 < ncol1; ++i2) {
            tmp_val_refv[i2].push_back(tmp1[i2][i]);
          };
          for (i2 = 0; i2 < ncol2; ++i2) {
            tmp_val_refv[i2 + ncol1].push_back("NA");
          };
          nrow += 1;
        };
      };
      for (i = 0; i < nrow2; ++i) {
        i2 = 0;
        cur_str = col2[i];
        while (i2 < nrow1) {
          if (cur_str == col1[i2]) {
            break;
          };
         i2 += 1;
        };
        if (i2 == nrow1) {
          for (i2 = 0; i2 < ncol1; ++i2) {
            tmp_val_refv[i2].push_back("NA");
          };
          for (i2 = 0; i2 < ncol2; ++i2) {
            tmp_val_refv[i2 + ncol1].push_back(tmp2[i2][i]);
          };
          nrow += 1;
        };
      };
      longest_determine();
    };

    void merge_all(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2) {
      unsigned int ncol1 = obj1.get_ncol();
      unsigned int ncol2 = obj2.get_ncol();
      std::vector<std::string> cur_vstr;
      ncol = ncol1 + ncol2;
      const unsigned int nrow1 = obj1.get_nrow();
      const unsigned int nrow2 = obj2.get_nrow();
      unsigned int i;
      unsigned int i2;
      unsigned int i3;
      std::vector<std::string> name1 = obj1.get_colname();
      std::vector<std::string> name2 = obj2.get_colname();
      if (colname) {
        name_v.resize(ncol);
        if (name1.size() > 0) {
          for (i = 0; i < name1.size(); ++i) {
            name_v.push_back(name1[i]);
          };
        };
        if (name2.size() > 0) {
          for (i = 0; i < name2.size(); ++i) {
            name_v.push_back(name2[i]);
          };
        };
      };
      tmp_val_refv.resize(ncol);
      for (i = 0; i < ncol; ++i) {
        tmp_val_refv.push_back(cur_vstr);
      };
      std::vector<const char*> type1 = obj1.get_typecol();
      std::vector<const char*> type2 = obj2.get_typecol();
      type_refv.reserve(ncol);
      for (i = 0; i < ncol1; ++i) {
        type_refv.push_back(type1[i]);
      };
      for (i = 0; i < ncol2; ++i) {
        type_refv.push_back(type2[i]);
      };
      std::vector<std::vector<std::string>> tmp1 = obj1.get_tmp_val_refv();
      std::vector<std::vector<std::string>> tmp2 = obj2.get_tmp_val_refv();
      std::vector<std::string> col1 = tmp1[key1];
      std::vector<std::string> col2 = tmp2[key2];
      std::string cur_str;
      for (i = 0; i < nrow1; ++i) {
        i2 = 0;
        cur_str = col1[i];
        while (i2 < nrow2) {
          if (cur_str == col2[i2]) {
            break;
          };
         i2 += 1;
        };
        if (i2 == nrow2) {
          for (i2 = 0; i2 < ncol1; ++i2) {
            tmp_val_refv[i2].push_back(tmp1[i2][i]);
          };
          for (i2 = 0; i2 < ncol2; ++i2) {
            tmp_val_refv[i2 + ncol1].push_back("NA");
          };
          nrow += 1;
        };
      };
      for (i = 0; i < nrow2; ++i) {
        i2 = 0;
        cur_str = col2[i];
        while (i2 < nrow1) {
          if (cur_str == col1[i2]) {
            break;
          };
         i2 += 1;
        };
        if (i2 == nrow1) {
          for (i2 = 0; i2 < ncol1; ++i2) {
            tmp_val_refv[i2].push_back("NA");
          };
          for (i2 = 0; i2 < ncol2; ++i2) {
            tmp_val_refv[i2 + ncol1].push_back(tmp2[i2][i]);
          };
          nrow += 1;
        };
      };
      for (i = 0; i < nrow1; ++i) {
        cur_str = col1[i];
        for (i2 = 0; i2 < nrow2; ++i2) {
          if (cur_str == col2[i2]) {
            for (i3 = 0; i3 < ncol1; ++i3) {
              tmp_val_refv[i3].push_back(tmp1[i3][i]);
            };
            for (i3 = 0; i3 < ncol2; ++i3) {
              tmp_val_refv[ncol1 + i3].push_back(tmp2[i3][i2]);
            };
            nrow += 1;
            break;
          };
        };
      };
      longest_determine();
    };

    void set_colname(std::vector<std::string> &x) {
      if (x.size() != ncol) {
        std::cout << "the number of columns of the dataframe does not correspond to the size of the input column name vector";
        return;
      } else {
        name_v = x;
      };
    };

    void set_rowname(std::vector<std::string> &x) {
      if (x.size() != nrow) {
        std::cout << "the number of columns of the dataframe does not correspond to the size of the input column name vector";
        return;
      } else {
        name_v_row = x;
      };
    };

    std::vector<std::string> get_colname() {
      return name_v;
    };

    std::vector<std::string> get_rowname() {
      return name_v_row;
    };

    std::vector<const char*> get_typecol() {
      return type_refv;
    };

    Dataframe() {};

    ~Dataframe() {};

};

//@L1 The Dataframe Object

//@T Dataframe
//@U Dataframe my_dataframe
//@X
//@D Dataframe objects supporting reading csv, with custom separator, storing columns in differents type vectors, creating a new Dataframe object on top of an already existing one specifying the rows and columns to copy, the same goes for a matrix (as <code>std::vector&lt;std::vector&lt;T&gt;&gt;</code>) and <code>std::vector&lt;T&gt;</code>. See examples.
//@A See_below : See below
//@X
//@E See below
//@X

//@T Dataframe.readf
//@U void readf(std::string &file_name, char delim = ',', bool header_name = 1, char str_context_begin = '\'', char str_context_end = '\'')
//@X
//@D Import a csv as a Dataframe object.
//@A file_name : is the file_name of the csv to read
//@A delim : is the column delimiter
//@A header_name : is if the first row is in fact the column names
//@A str_context_begin : is the first symbol of a quote, (to not take in count a comma as a new column if it is in a quote for example)
//@A str_context_end : is the end symbol for a quote context
//@X
//@E Dataframe obj1;
//@E std::string file_name = "teste_dataframe.csv";
//@E obj1.readf(file_name);
//@X

//@T Dataframe.writef
//@U void writef(std::string &file_name, char delim = ',', bool header_name = 1, char str_context_bgn = '\'', char str_context_end = '\'')
//@X
//@D Write a dataframe object into a csv file.
//@A file_name : is the file name to write data into
//@A delim : is the column delimiter
//@A header_name : 1 to write the column names, 0 else
//@A str_context_begin : is the first symbol of a quote, (to not take in count a comma as a new column if it is in a quote for example)
//@A str_context_end : is the end symbol for a quote context
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::string out_file = "out.csv";
//@E obj1.writef(out_file);
//@X

//@T Dataframe.display
//@U void display();
//@X
//@D Print the current dataframe.
//@A no : no
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E obj1.display();
//@E &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;
//@E col1 col2 col3 col4 col5 col6
//@E :0:  1    2    3    aa   5    z
//@E :1:  6    7    8    bb   10   e
//@E :2:  1    2    3    cc   5    h
//@E :3:  6    7    8    uu   10   a
//@E :4:  1    2    3    s4   -5   q
//@E :5:  6    7    8    s9   10   p
//@E :6:  1    2    3    a4   5    j
//@E :7:  6    7    8    m9   10   i
//@E :8:  6    7    8    s9   10   p
//@E :9:  1    2    3    a4   5    j
//@E :10: 6    7    8    m9   10   i
//@E :11: 6    7    8    m9   10   i
//@E :12: 6    7    8    s9   10   p
//@E :13: 1    2    3    a4   5    j
//@E :14: 6    7    8    m9   10   i
//@M img_dataframe.jpg
//@X

//@T Dataframe.idx_dataframe
//@U void idx_dataframe(std::vector&lt;int&gt; &rows, std::vector&lt;int&gt; &cols, Dataframe &cur_obj)
//@X
//@D Allow to copy a dataframe choosing rows and columns (by index) of the copied dataframe. 
//@A rows : is the vector containing all the rows to copy (<code>{-1}</code>) for all
//@A cols : is the vector of the index of the columns to copy
//@A cur_obj : is the dataframe that will contain all the rows and columns of the copied dataframe
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E Dataframe obj2;
//@E std::vector&lt;int&gt; idx_rows = {-1};
//@E std::vector&lt;int&gt; idx_cols2 = {1, 2, 3};
//@E obj2.idx_dataframe(idx_rows, idx_cols2, obj1);
//@E 
//@E obj2.display();
//@E     col1 col2 col3
//@E :0:  2    3    aa
//@E :1:  7    8    bb
//@E :2:  2    3    cc
//@E :3:  7    8    uu
//@E :4:  2    3    s4
//@E :5:  7    8    s9
//@E :6:  2    3    a4
//@E :7:  7    8    m9
//@E :8:  7    8    s9
//@E :9:  2    3    a4
//@E :10: 7    8    m9
//@E :11: 7    8    m9
//@E :12: 7    8    s9
//@E :13: 2    3    a4
//@E :14: 7    8    m9
//@X

//@T Dataframe.name_dataframe
//@U void name_dataframe(std::vector&lt;int&gt; &rows, std::vector&lt;int&gt; &name_cols, Dataframe &cur_obj)
//@X
//@D Allow to copy a dataframe choosing rows and columns (by name) of the copied dataframe. 
//@A rows : is the vector containing all the rows to copy (<code>{-1}</code>) for all
//@A cols : is the vector of the name of the columns to copy
//@A cur_obj : is the dataframe that will contain all the rows and columns of the copied dataframe
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E Dataframe obj2;
//@E std::vector&lt;int&gt; idx_rows = {-1};
//@E std::vector&lt;std::string&gt; idx_cols2 = {"col2", "col3", "col3"};
//@E obj2.name_dataframe(idx_rows, idx_cols2, obj1);
//@E 
//@E obj2.display();
//@E     col1 col2 col3
//@E :0:  2    3    aa
//@E :1:  7    8    bb
//@E :2:  2    3    cc
//@E :3:  7    8    uu
//@E :4:  2    3    s4
//@E :5:  7    8    s9
//@E :6:  2    3    a4
//@E :7:  7    8    m9
//@E :8:  7    8    s9
//@E :9:  2    3    a4
//@E :10: 7    8    m9
//@E :11: 7    8    m9
//@E :12: 7    8    s9
//@E :13: 2    3    a4
//@E :14: 7    8    m9
//@X

//@T Dataframe.idx_colint
//@U template &lt;typename T&gt; void idx_colint(std::vector&lt;int&gt; rows, unsigned int x, std::vector&lt;T&gt; &rtn_v)
//@X
//@D Allow to copy a int, unsigned int , bool or double column as a vector&lt;T&gt;, by column index.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x : is the index of the column to copy
//@A rtn_v : is the vector that will contain the column to copy
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;int&gt; currows = {1, 0, 1};
//@E std::vector&lt;unsigned int&gt; outv = {};
//@E obj1.idx_colint(currows, 2, outv);
//@E print_nvec(outv);
//@E :0: 8 3 8
//@X

//@T Dataframe.name_colint
//@U template &lt;typename T&gt; void name_colint(std::vector&lt;int&gt; rows, std::string colname, std::vector&lt;T&gt; &rtn_v)
//@X
//@D Allow to copy a int, unsigned int , bool or double column as a vector&lt;T&gt;, by column name.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x : is the name of the column to copy
//@A rtn_v : is the vector that will contain the column to copy
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;int&gt; currows = {1, 0, 1};
//@E std::vector&lt;unsigned int&gt; outv = {};
//@E obj1.idx_colint(currows, "col2", outv);
//@E print_nvec(outv);
//@E :0: 8 3 8
//@X

//@T Dataframe.idx_colstr
//@U void idx_colstr(std::vector&lt;int&gt; rows, unsigned int x, std::vector&lt;std::string&gt; &rtn_v)
//@X
//@D Allow to copy a std::string column as a vector&lt;std::string&gt;, by column index.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x : is the index of the column to copy
//@A rtn_v : is the vector that will contain the column to copy
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::string&gt; outv2 = {};
//@E obj1.idx_colstr(currows, 3, outv2);
//@E print_svec(outv2);
//@E :0: bb aa bb
//@X

//@T Dataframe.name_colstr
//@U template &lt;typename T&gt; void name_colint(std::vector&lt;int&gt; rows, std::string colname, std::vector&lt;T&gt; &rtn_v)
//@X
//@D Allow to copy a int, unsigned int , bool or double column as a vector&lt;std::string&gt;, by column name.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x : is the name of the column to copy
//@A rtn_v : is the vector that will contain the column to copy
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::string&gt; outv2 = {};
//@E obj1.name_colstr(currows, "col4", outv2);
//@E print_svec(outv2);
//@E :0: bb aa bb
//@X

//@T Dataframe.idx_colchr
//@U void idx_colchr(std::vector&lt;int&gt; rows, unsigned int x, std::vector&lt;char&gt; &rtn_v)
//@X
//@D Allow to copy a char column as a vector&lt;char&gt;, by column index.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x : is the index of the column to copy
//@A rtn_v : is the vector that will contain the column to copy
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;char&gt; outv3 = {};
//@E obj1.idx_colchr(currows, 5, outv3);
//@E for (char i : outv3) {
//@E   std::cout &lt;&lt; i &lt;&lt; " ";
//@E };
//@E std::cout &lt;&lt; "\n";
//@E e z e
//@X

//@T Dataframe.name_colchr
//@U void name_colchr(std::vector&lt;int&gt; rows, std::string colname, std::vector&lt;char&gt; &rtn_v)
//@X
//@D Allow to copy a char column as a vector&lt;char&gt;, by column name.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x : is the name of the column to copy
//@A rtn_v : is the vector that will contain the column to copy
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;char&gt; outv3 = {};
//@E obj1.name_colchr(currows, "col6", outv3);
//@E for (char i : outv3) {
//@E   std::cout &lt;&lt; i &lt;&lt; " ";
//@E };
//@E std::cout &lt;&lt; "\n";
//@E e z e
//@X

//@T Dataframe.idx_matrint
//@U template &lt;typename T&gt; void idx_matrint(std::vector&lt;int&gt; rows, std::vector&lt;unsigned int&gt; x_v, std::vector&lt;std::vector&lt;T&gt;&gt; &rtn_matr)
//@X
//@D Allow to copy a set of columns that are same type (int, unsigned int, bool or double) as a <code> std::vector&lt;std::vector&lt;T&gt;&gt; </code>, by column index.
//@A rows : is a vector containing the row indices to copy (<code> {-1} </code>) for all
//@A x_v : is the vector containing the indices of the column to copy
//@A rtn_matr : is the matrix that will contain all the columns copyed
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::vector&lt;unsigned int&gt;&gt; out_matr = {};
//@E std::vector&lt;unsigned int&gt; idx_cols = {1, 0, 2, 2};
//@E obj1.idx_matrint(currows, idx_cols, out_matr);
//@E print_nmatr(out_matr);
//@E                   [0]               [1]               [2]               [3]
//@E :0:                 7                 6                 8                 8
//@E :1:                 2                 1                 3                 3
//@E :2:                 7                 6                 8                 8
//@X

//@T Dataframe.name_matrint
//@U template &lt;typename T&gt; void name_matrint(std::vector&lt;int&gt; rows, std::vector&lt;std::string&gt; x_v, std::vector&lt;std::vector&lt;T&gt;&gt; &rtn_matr)
//@X
//@D Allow to copy a set of columns that are same type (int, unsigned int, bool or double) as a <code>std::vector&lt;std::vector&lt;T&gt;&gt;</code>, by column name.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x_v : is the vector containing the names of the column to copy
//@A rtn_matr : is the matrix that will contain all the columns copyed
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::vector&lt;unsigned int&gt;&gt; out_matr = {};
//@E std::vector&lt;std::string&gt; idx_vec2 = {"col1", "col2", "col3"};
//@E obj1.name_matrint(currows, idx_vec2, out_matr);
//@E print_nmatr(out_matr);
//@E                   [0]               [1]               [2]
//@E :0:                 6                 7                 8
//@E :1:                 1                 2                 3
//@E :2:                 6                 7                 8
//@X

//@T Dataframe.idx_matrstr
//@U void idx_matrstr(std::vector&lt;int&gt; rows, std::vector&lt;unsigned int&gt; x_v, std::vector&lt;std::vector&lt;std::string&gt;&gt; &rtn_matr)
//@X
//@D Allow to copy a set of columns that are <code>std::string</code> type as a <code>std::vector&lt;std::vector&lt;std::string&gt;&gt;</code>, by column index.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x_v : is the vector containing the indices of the column to copy
//@A rtn_matr : is the matrix that will contain all the columns copyed
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::vector&lt;std::string&gt;&gt; out_matr2 = {};
//@E std::vector&lt;unsigned int&gt; idx_cols = {3};
//@E obj1.idx_matrstr(currows, idx_cols, out_matr2);
//@E print_smatr(out_matr2);
//@E                     [0]
//@E :0:                   bb
//@E :1:                   aa
//@E :2:                   bb
//@X

//@T Dataframe.name_matrstr
//@U void name_matrstr(std::vector&lt;int&gt; rows, std::vector&lt;std::string&gt; x_v, std::vector&lt;std::vector&lt;std::string&gt;&gt; &rtn_matr)
//@X
//@D Allow to copy a set of columns that are <code>std::string</code> type as a <code>std::vector&lt;std::vector&lt;std::string&gt;&gt;</code>, by column name.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x_v : is the vector containing the names of the column to copy
//@A rtn_matr : is the matrix that will contain all the columns copyed
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::vector&lt;std::string&gt;&gt; out_matr2 = {};
//@E std::vector&lt;std::string&gt; idx_vec2 = {"col4"};
//@E obj1.name_matrstr(currows, idx_vec2, out_matr2);
//@E print_smatr(out_matr2);
//@E                     [0]
//@E :0:                   bb
//@E :1:                   aa
//@E :2:                   bb
//@X

//@T Dataframe.idx_matrchr
//@U void idx_matrchr(std::vector&lt;int&gt; rows, std::vector&lt;unsigned int&gt; x_v, std::vector&lt;std::vector&lt;char&gt;&gt; &rtn_matr)
//@X
//@D Allow to copy a set of columns that are <code>char</code> type as a <code>std::vector&lt;std::vector&lt;char&gt;&gt;</code>, by column index.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x_v : is the vector containing the indices of the column to copy
//@A rtn_matr : is the matrix that will contain all the columns copyed
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::vector&lt;char&gt;&gt; out_matr3 = {};
//@E std::vector&lt;unsigned int&gt; idx_cols = {5};
//@E obj1.idx_matrchr(currows, idx_cols, out_matr3);
//@E print_smatr(out_matr3);
//@E                     [0]
//@E :0:                    e
//@E :1:                    z
//@E :2:                    e
//@X

//@T Dataframe.name_matrchr
//@U void name_matrchr(std::vector&lt;int&gt; rows, std::vector&lt;std::string&gt; x_v, std::vector&lt;std::vector&lt;char&gt;&gt; &rtn_matr)
//@X
//@D Allow to copy a set of columns that are <code>char</code> type as a <code>std::vector&lt;std::vector&lt;char&gt;&gt;</code>, by column name.
//@A rows : is a vector containing the row indices to copy (<code>{-1}</code>) for all
//@A x_v : is the vector containing the names of the column to copy
//@A rtn_matr : is the matrix that will contain all the columns copyed
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;char&gt; out_matr3 = {};
//@E std::vector&lt;std::string&gt; idx_vec2 = {"col6"};
//@E obj1.name_matrchr(currows, idx_vec2, out_matr3);
//@E print_smatr(out_matr3);
//@E                     [0]
//@E :0:                    e
//@E :1:                    z
//@E :2:                    e
//@X

//@T Dataframe.get_nrow
//@U unsigned int get_nrow();
//@X
//@D Returns the number of rows for the associated dataframe.
//@E // after reading teste_dataframe.csv as obj1
//@E unsigned int nrow = obj1.get_nrow();
//@E 15
//@X

//@T Dataframe.get_ncol
//@U unsigned int get_ncol();
//@X
//@D Returns the number of columns for the associated dataframe.
//@E // after reading teste_dataframe.csv as obj1
//@E unsigned int ncol = obj1.get_ncol();
//@E 6
//@X

//@T Dataframe.get_rowname
//@U std::vector&lt;std::string&gt; get_rowname();
//@X
//@D Returns the rowname of the associated dataframe.
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::string&gt; row_names = obj1.get_rowname();
//@E nothing becuase obj1 has no rownames
//@X

//@T Dataframe.get_colname
//@U std::vector&lt;std::string&gt; get_colname();
//@X
//@D Returns the colname of the associated dataframe.
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::string&gt; col_names = obj1.get_colname();
//@E col1 col2 col3 col4 col5 col6
//@X

//@T Dataframe.set_rowname
//@U void set_rowname(std::vector&lt;std::string&gt; &x);
//@X
//@D Set rowname to the associated dataframe.
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::string&gt; row_names = {"n1", "n2", "n3"..."n15"};
//@E obj1.set_rowname(row_names);
//@X

//@T Dataframe.set_colname
//@U void set_colname(std::vector&lt;std::string&gt; &x);
//@X
//@D Set colname to the associated dataframe.
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;std::string&gt; col_names = {"col1", "col2", "col3", "col4", 
//@E "col5", "col6"};
//@E obj1.set_colname();
//@X

//@T Dataframe.replace_colint
//@U template &lt;typename T&gt; void replace_colint(std::vector&lt;T&gt; &x, unsigned int &colnb)
//@X
//@D Replace a int, unsigned int, bool or double column of the associated dataframe.
//@A x : is the column (as vector) that will replace the dataframe column
//@A colnb : is the index of the column to replace
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E 
//@E std::vector&lt;unsigned int&gt; rpl_col = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 
//@E                                       10, 11, 12, 13, 14};
//@E unsigned int col = 0;
//@E obj1.replace_colint(rpl_col, col);
//@E obj1.display();
//@E      &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;
//@E      col1   col2   col3   col4  col5  col6
//@E  :0:  0      2      3      aa    5     z
//@E  :1:  1      7      8      bb    10    e
//@E  :2:  2      2      3      cc    5     h
//@E  :3:  3      7      8      uu    10    a
//@E  :4:  4      2      3      s4    -5    q
//@E  :5:  5      7      8      s9    10    p
//@E  :6:  6      2      3      a4    5     j
//@E  :7:  7      7      8      m9    10    i
//@E  :8:  8      7      8      s9    10    p
//@E  :9:  9      2      3      a4    5     j
//@E  :10: 10     7      8      m9    10    i
//@E  :11: 11     7      8      m9    10    i
//@E  :12: 12     7      8      s9    10    p
//@E  :13: 13     2      3      NA    5     j
//@E  :14: 14     7      8      m9    10    i
//@X

//@T Dataframe.replace_colstr
//@U void replace_colstr(std::vector&lt;std::string&gt; &x, unsigned int &colnb)
//@X
//@D Replace a string column of the associated dataframe.
//@A x : is the column (as vector) that will replace the dataframe column
//@A colnb : is the index of the column to replace
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E
//@E std::vector&lt;std::string&gt; rpl_col = {"0", "1", "2", "3", "4", "5", "6", 
//@E                                         "7", "8", "9", 
//@E                                         "10", "11", "12", "13", "14"};
//@E unsigned int col = 3;
//@E obj1.replace_colstr(rpl_col, col);
//@E obj1.display();
//@E     &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;
//@E     col1   col2   col3   col4  col5  col6
//@E :0:  1      2      3      0     5     z
//@E :1:  6      7      8      1     10    e
//@E :2:  1      2      3      2     5     h
//@E :3:  6      7      8      3     10    a
//@E :4:  1      2      3      4     -5    q
//@E :5:  6      7      8      5     10    p
//@E :6:  1      2      3      6     5     j
//@E :7:  6      7      8      7     10    i
//@E :8:  6      7      8      8     10    p
//@E :9:  1      2      3      9     5     j
//@E :10: 6      7      8      10    10    i
//@E :11: 6      7      8      11    10    i
//@E :12: 6      7      8      12    10    p
//@E :13: 1      2      3      13    5     j
//@E :14: 6      7      8      14    10    i
//@X

//@T Dataframe.replace_colchr
//@U void replace_colchr(std::vector&lt;char&gt; &x, unsigned int &colnb)
//@X
//@D Replace a string column of the associated dataframe.
//@A x : is the column (as vector) that will replace the dataframe column
//@A colnb : is the index of the column to replace
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E
//@E std::vector&lt;char&gt; rpl_col = {'c', 'c', 'c', 'c', 'c', 'c', 'c', 
//@E                                       'c', 'c', 'c', 
//@E                                       'b', 'b', 'v', 'v', 'v'};
//@E unsigned int col = 5;
//@E obj1.replace_colchr(rpl_col, col);
//@E obj1.display();
//@E     &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;
//@E     col1   col2   col3   col4  col5  col6
//@E :0:  1      2      3      aa    5     c
//@E :1:  6      7      8      bb    10    c
//@E :2:  1      2      3      cc    5     c
//@E :3:  6      7      8      uu    10    c
//@E :4:  1      2      3      s4    -5    c
//@E :5:  6      7      8      s9    10    c
//@E :6:  1      2      3      a4    5     c
//@E :7:  6      7      8      m9    10    c
//@E :8:  6      7      8      s9    10    c
//@E :9:  1      2      3      a4    5     c
//@E :10: 6      7      8      m9    10    b
//@E :11: 6      7      8      m9    10    b
//@E :12: 6      7      8      s9    10    v
//@E :13: 1      2      3      NA    5     v
//@E :14: 6      7      8      m9    10    v
//@X

//@T Dataframe.add_colint
//@U template &lt;typename T&gt; void add_colint(std::vector&lt;T&gt; &x, std::string name = "NA")
//@X
//@D Add a column int, unsigned int, bool or double type to the associated dataframe
//@A x : is the column to add
//@A name : is the column to add name
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;unsigned int&gt; rpl_col = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 
//@E                                       10, 11, 12, 13, 14};
//@E obj1.add_colint(rpl_col);
//@E obj1.display();
//@E     &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt; &lt;uint&gt;
//@E     col1   col2   col3   col4  col5  col6   NA
//@E :0:  1      2      3      aa    5     z      0
//@E :1:  6      7      8      bb    10    e      1
//@E :2:  1      2      3      cc    5     h      2
//@E :3:  6      7      8      uu    10    a      3
//@E :4:  1      2      3      s4    -5    q      4
//@E :5:  6      7      8      s9    10    p      5
//@E :6:  1      2      3      a4    5     j      6
//@E :7:  6      7      8      m9    10    i      7
//@E :8:  6      7      8      s9    10    p      8
//@E :9:  1      2      3      a4    5     j      9
//@E :10: 6      7      8      m9    10    i      10
//@E :11: 6      7      8      m9    10    i      11
//@E :12: 6      7      8      s9    10    p      12
//@E :13: 1      2      3      NA    5     j      13
//@E :14: 6      7      8      m9    10    i      14
//@X

//@T Dataframe.add_colstr
//@U void add_colstr(std::vector&lt;std::string&gt; &x, std::string name = "NA")
//@X
//@D Add a column string type to the associated dataframe.
//@A x : is the column to add
//@A name : is the column to add name
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E 
//@E std::vector&lt;std::string&gt; rpl_col = {"0", "1", "2", "3", "4", "5", "6", "7", "8", "9", 
//@E                                       "10", "11", "12", "13", "14"};
//@E obj1.add_colstr(rpl_col);
//@E obj1.display();
//@E     &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt; &lt;str&gt;
//@E     col1   col2   col3   col4  col5  col6   NA
//@E :0:  1      2      3      aa    5     z      0
//@E :1:  6      7      8      bb    10    e      1
//@E :2:  1      2      3      cc    5     h      2
//@E :3:  6      7      8      uu    10    a      3
//@E :4:  1      2      3      s4    -5    q      4
//@E :5:  6      7      8      s9    10    p      5
//@E :6:  1      2      3      a4    5     j      6
//@E :7:  6      7      8      m9    10    i      7
//@E :8:  6      7      8      s9    10    p      8
//@E :9:  1      2      3      a4    5     j      9
//@E :10: 6      7      8      m9    10    i      10
//@E :11: 6      7      8      m9    10    i      11
//@E :12: 6      7      8      s9    10    p      12
//@E :13: 1      2      3      NA    5     j      13
//@E :14: 6      7      8      m9    10    i      14
//@X

//@T Dataframe.add_colchr
//@U add_colchr(std::vector&lt;char&gt; &x, std::string name = "NA")
//@X
//@D Add a column char type to the associated dataframe.
//@A x : is the column to add
//@A name : is the column to add name
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;char&gt; rpl_col = {'c', 'c', 'c', 'c', 'c', 'c', 'c', 
//@E                                       'c', 'c', 'c', 
//@E                                       'b', 'b', 'v', 'v', 'v'};
//@E obj1.add_colchr(rpl_col);
//@E obj1.display();
//@E     &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt; &lt;char&gt;
//@E     col1   col2   col3   col4  col5  col6   NA
//@E :0:  1      2      3      aa    5     z      c
//@E :1:  6      7      8      bb    10    e      c
//@E :2:  1      2      3      cc    5     h      c
//@E :3:  6      7      8      uu    10    a      c
//@E :4:  1      2      3      s4    -5    q      c
//@E :5:  6      7      8      s9    10    p      c
//@E :6:  1      2      3      a4    5     j      c
//@E :7:  6      7      8      m9    10    i      c
//@E :8:  6      7      8      s9    10    p      c
//@E :9:  1      2      3      a4    5     j      c
//@E :10: 6      7      8      m9    10    i      b
//@E :11: 6      7      8      m9    10    i      b
//@E :12: 6      7      8      s9    10    p      v
//@E :13: 1      2      3      NA    5     j      v
//@E :14: 6      7      8      m9    10    i      v
//@X

//@T Dataframe.rm_col
//@U void rm_col(std::vector&lt;unsigned int&gt; &nbcolv)
//@X
//@D Removes columns from associated dataframe.
//@A nbcolv : is a vector containing all the indices of the columns to erase from the associated dataframe. The indices must be sorted descendly.
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;unsigned int&gt; colv = {4, 1};
//@E obj1.rm_col(colv);
//@E obj1.display();
//@E     &lt;uint&gt; &lt;uint&gt; &lt;str&gt;  &lt;char&gt;
//@E     col1   col3   col4   col6
//@E :0:  1      3      aa     z
//@E :1:  6      8      bb     e
//@E :2:  1      3      cc     h
//@E :3:  6      8      uu     a
//@E :4:  1      3      s4     q
//@E :5:  6      8      s9     p
//@E :6:  1      3      a4     j
//@E :7:  6      8      m9     i
//@E :8:  6      8      s9     p
//@E :9:  1      3      a4     j
//@E :10: 6      8      m9     i
//@E :11: 6      8      m9     i
//@E :12: 6      8      s9     p
//@E :13: 1      3      NA     j
//@E :14: 6      8      m9     i
//@X

//@T Dataframe.rm_row
//@U void rm_col(std::vector&lt;unsigned int&gt; &nbcolv)
//@X
//@D Removes rows from associated dataframe.
//@A nbcolv : is a vector containing all the indices of the rows to erase from the associated dataframe. The indices must be sorted descendly.
//@X
//@E // after reading teste_dataframe.csv as obj1
//@E std::vector&lt;unsigned int&gt; rowv = {4, 1};
//@E obj1.rm_row(rowv);
//@E obj1.display();
//@E     &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;
//@E     col1   col2   col3   col4  col5  col6
//@E :0:  1      2      3      aa    5     z
//@E :1:  1      2      3      cc    5     h
//@E :2:  6      7      8      uu    10    a
//@E :3:  6      7      8      s9    10    p
//@E :4:  1      2      3      a4    5     j
//@E :5:  6      7      8      m9    10    i
//@E :6:  6      7      8      s9    10    p
//@E :7:  1      2      3      a4    5     j
//@E :8:  6      7      8      m9    10    i
//@E :9:  6      7      8      m9    10    i
//@E :10: 6      7      8      s9    10    p
//@E :11: 1      2      3      NA    5     j
//@E :12: 6      7      8      m9    10    i
//@X

//@T Dataframe.transform_inner
//@U void transform_inner(Dataframe &cur_obj, unsigned int &in_col, unsigned int &ext_col)
//@X
//@D Applies a inner join on the associated dataframe.
//@A cur_obj : is the other dataframe used for inner join
//@A in_col : is the index of the column representing the key (primary) of the associated dataframe
//@A ext_col : is the index of the column representing the key (foreign) of the other dataframe used for the inner join
//@X
//@E
//@E Dataframe obj1, obj2;
//@E std::string filename = "outb.csv";
//@E obj1.readf(filename);
//@E 
//@E std::vector&lt;unsigned int&gt; colv = {4, 3, 2};
//@E obj1.rm_col(colv);
//@E 
//@E std::string f2 = "outb2.csv";
//@E obj2.readf(f2);
//@E 
//@E unsigned int col1 = 0;
//@E unsigned int col2 = 0;
//@E 
//@E obj1.transform_inner(obj2, col1, col2);
//@E obj1.display();
//@E  &lt;str&gt; &lt;uint&gt;
//@E     col1  col2
//@E :0:  id1   1
//@E :1:  id2   6
//@E :2:  id4   6
//@E :3:  id5   1
//@E :4:  id6   6
//@E :5:  id7   1
//@E :6:  id8   6
//@E :7:  id9   6
//@E :8:  id11  6
//@E :9:  id12  6
//@E :10: id14  1
//@E :11: id15  6
//@X

//@T Dataframe.transform_excluding
//@U void transform_excluding(Dataframe &cur_obj, unsigned int &in_col, unsigned int &ext_col)
//@X
//@D Applies a excluding join on the associated dataframe.
//@A cur_obj : is the other dataframe used for the excluding join
//@A in_col : is the index of the column representing the key (primary) of the associated dataframe
//@A ext_col : is the index of the column representing the key (foreign) of the other dataframe used for the excluding join
//@X
//@E
//@E Dataframe obj1, obj2;
//@E std::string filename = "outb.csv";
//@E obj1.readf(filename);
//@E 
//@E std::vector&lt;unsigned int&gt; colv = {4, 3, 2};
//@E obj1.rm_col(colv);
//@E 
//@E std::string f2 = "outb2.csv";
//@E obj2.readf(f2);
//@E 
//@E unsigned int col1 = 0;
//@E unsigned int col2 = 0;
//@E 
//@E obj1.transform_excluding(obj2, col1, col2);
//@E obj1.display();
//@E    &lt;str&gt; &lt;uint&gt;
//@E    col1  col2
//@E :0: id3   1
//@E :1: id10  1
//@E :2: id13  6
//@X

//@T Dataframe.merge_inner
//@U void merge_inner(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2)
//@X
//@D Performs a inner join on a newly created dataframe.
//@A obj1 : is the first dataframe
//@A obj2 : is the second dataframe
//@A colname : 1 to give the column names to the newly created dataframe
//@A key1 : is the index of the first dataframe column as primary key
//@A key1 : is the index of the first dataframe column as foreign key
//@X
//@E 
//@E Dataframe obj1, obj2, obj3;
//@E std::string filename = "outb.csv";
//@E obj1.readf(filename);
//@E 
//@E std::vector&lt;unsigned int&gt; colv = {4, 3, 2};
//@E obj1.rm_col(colv);
//@E 
//@E std::string f2 = "outb2.csv";
//@E obj2.readf(f2);
//@E 
//@E unsigned int col1 = 0;
//@E unsigned int col2 = 0;
//@E 
//@E obj3.merge_inner(obj1, obj2, 1, col1, col2);
//@E obj3.display();
//@E     &lt;str&gt; &lt;uint&gt; &lt;str&gt; &lt;uint&gt; &lt;uint&gt;
//@E 
//@E :0:  id1   1      id1   2      3
//@E :1:  id2   6      id2   7      8
//@E :2:  id4   6      id4   7      8
//@E :3:  id5   1      id5   2      3
//@E :4:  id6   6      id6   7      8
//@E :5:  id7   1      id7   2      3
//@E :6:  id8   6      id8   2      3
//@E :7:  id9   6      id9   7      8
//@E :8:  id11  6      id11  7      8
//@E :9:  id12  6      id12  7      8
//@E :10: id14  1      id14  7      8
//@E :11: id15  6      id15  2      3
//@X

//@T Dataframe.merge_excluding
//@U void merge_excluding(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2)
//@X
//@D Performs a left excluding join to the associated dataframe (newly created). The first dataframe as argument is considered as the left one.
//@A obj1 : is the left dataframe
//@A obj2 : is the right dataframe
//@A colname : 1 to give the column names to the newly created dataframe
//@A key1 : is the index of the column of the left dataframe
//@A key2 : is the index of the column of the right dataframe
//@X
//@E Dataframe obj1, obj2, obj3;
//@E std::string filename = "outb.csv";
//@E obj1.readf(filename);
//@E 
//@E std::vector&lt;unsigned int&gt; colv = {4, 3, 2};
//@E obj1.rm_col(colv);
//@E 
//@E std::string f2 = "outb2.csv";
//@E obj2.readf(f2);
//@E 
//@E unsigned int col1 = 0;
//@E unsigned int col2 = 0;
//@E 
//@E obj3.merge_excluding(obj1, obj2, 1, col1, col2);
//@E obj3.display();
//@E    &lt;str&gt; &lt;uint&gt; &lt;str&gt; &lt;uint&gt; &lt;uint&gt;
//@E 
//@E :0: id3   1      NA    NA     NA
//@E :1: id10  1      NA    NA     NA
//@E :2: id13  6      NA    NA     NA
//@X

//@T Dataframe.merge_excluding_both
//@U void merge_excluding_both(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2)
//@X
//@D Performs a full excluding join to the associated dataframe (newly created). The first dataframe as argument is considered as the left one.
//@A obj1 : is the left dataframe
//@A obj2 : is the right dataframe
//@A colname : 1 to give the column names to the newly created dataframe
//@A key1 : is the index of the column of the left dataframe
//@A key2 : is the index of the column of the right dataframe
//@X
//@E Dataframe obj1, obj2, obj3;
//@E std::string filename = "outb.csv";
//@E obj1.readf(filename);
//@E 
//@E std::vector&lt;unsigned int&gt; colv = {4, 3, 2};
//@E obj1.rm_col(colv);
//@E 
//@E std::string f2 = "outb2.csv";
//@E obj2.readf(f2);
//@E 
//@E unsigned int col1 = 0;
//@E unsigned int col2 = 0;
//@E 
//@E obj3.merge_excluding_both(obj1, obj2, 1, col1, col2);
//@E obj3.display();
//@E    &lt;str&gt; &lt;uint&gt; &lt;str&gt; &lt;uint&gt; &lt;uint&gt;
//@E 
//@E :0: id3   1      NA    NA     NA
//@E :1: id10  1      NA    NA     NA
//@E :2: id13  6      NA    NA     NA
//@E :3: NA    NA     id119 7      8
//@X

//@T Dataframe.merge_all
//@U void merge_all(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2)
//@X
//@D Performs a full join to the associated dataframe (newly created). The first dataframe as argument is considered as the left one.
//@A obj1 : is the left dataframe
//@A obj2 : is the right dataframe
//@A colname : 1 to give the column names to the newly created dataframe
//@A key1 : is the index of the column of the left dataframe
//@A key2 : is the index of the column of the right dataframe
//@X
//@E Dataframe obj1, obj2, obj3;
//@E std::string filename = "outb.csv";
//@E obj1.readf(filename);
//@E 
//@E std::vector&lt;unsigned int&gt; colv = {4, 3, 2};
//@E obj1.rm_col(colv);
//@E 
//@E std::string f2 = "outb2.csv";
//@E obj2.readf(f2);
//@E 
//@E unsigned int col1 = 0;
//@E unsigned int col2 = 0;
//@E 
//@E obj3.merge_all(obj1, obj2, 1, col1, col2);
//@E obj3.display();
//@E     &lt;str&gt; &lt;uint&gt; &lt;str&gt; &lt;uint&gt; &lt;uint&gt;
//@E 
//@E :0:  id3   1      NA    NA     NA
//@E :1:  id10  1      NA    NA     NA
//@E :2:  id13  6      NA    NA     NA
//@E :3:  NA    NA     id119 7      8
//@E :4:  id1   1      id1   2      3
//@E :5:  id2   6      id2   7      8
//@E :6:  id4   6      id4   7      8
//@E :7:  id5   1      id5   2      3
//@E :8:  id6   6      id6   7      8
//@E :9:  id7   1      id7   2      3
//@E :10: id8   6      id8   2      3
//@E :11: id9   6      id9   7      8
//@E :12: id11  6      id11  7      8
//@E :13: id12  6      id12  7      8
//@E :14: id14  1      id14  7      8
//@E :15: id15  6      id15  2      3
//@X



